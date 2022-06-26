# Symfony Docker Compose
This project is for using Docker in Symfony

## Requirements
    Symfony 6.1
    PHP 8.1
    MariaDB
    Nginx
    Docker
    Docker compose

## How to install

Download and install Docker & Docker Compose at https://docs.docker.com/get-docker/


1. Build Docker Compose

```
➜  symfonyDockerCompose git:(main) ✗ docker-compose up -d
[+] Running 4/4
 ⠿ Network symfonydockercompose_default        Created                                                                                                                                                           0.0s
 ⠿ Container symfonydockercompose-php-fpm-1    Started                                                                                                                                                           0.7s
 ⠿ Container symfonydockercompose-mariadb-1    Started                                                                                                                                                           0.8s
 ⠿ Container symfonydockercompose-webserver-1  Started                                                                                                                                                           0.8s
 ```

2. List all running containers

```
➜  symfonyDockerCompose git:(main) ✗ docker ps
CONTAINER ID   IMAGE                          COMMAND                  CREATED              STATUS              PORTS                    NAMES
f8d0f04a4ec0   nginx:alpine                   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8000->80/tcp     symfonydockercompose-webserver-1
a7a01f025d85   symfonydockercompose_php-fpm   "/usr/sbin/php-fpm8.…"   About a minute ago   Up About a minute   9000/tcp                 symfonydockercompose-php-fpm-1
171e9f59bdba   mariadb:10.6                   "docker-entrypoint.s…"   About a minute ago   Up 3 seconds        0.0.0.0:8003->3306/tcp   symfonydockercompose-mariadb-1
```

3. Terminate all containers
```
➜  symfonyDockerCompose git:(main) ✗ docker-compose down
[+] Running 4/3
 ⠿ Container symfonydockercompose-mariadb-1    Removed                                                                                                                                                           0.4s
 ⠿ Container symfonydockercompose-php-fpm-1    Removed                                                                                                                                                           0.2s
 ⠿ Container symfonydockercompose-webserver-1  Removed                                                                                                                                                           0.2s
 ⠿ Network symfonydockercompose_default        Removed                                                                                                                                                           0.0s
```

## How to

1. Attach to an instance
```
➜  symfonyDockerCompose git:(main) ✗ docker exec -it symfonydockercompose-php-fpm-1 bash
root@a7a01f025d85:/application# ls
README.md  bin  composer.json  composer.lock  config  docker-compose.yml  migrations  phpdocker  public  src  symfony.lock  var  vendor
```

2. Connect MariaDB from PHP
```
DATABASE_URL="mysql://root:root@mariadb:3306/app"
```

3. Change php.ini
```
./phpdocker/php-fpm/php-ini-overrides.ini
```
4. Access to webserver

The location is: http://localhost:8000/

5. Connect to MariaDB

- Host: 127.0.0.1
- Port: 8003
- User: app
- Password: root


## License

MIT
