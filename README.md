# jobs-dock

This project is made for local development

Using docker-compose

services like

- jobs-app
- nginx
- mysql
- phpMyAdmin
- redis

are created and started via docker containers defined in docker-compose.yaml

## Requirements for local development

- any linux dist with Docker capabilities
- Windows
  - WSL2
    - needs to be installed on WSL2
      - docker-compose
      - buildx
  - Docker Destkop
- hosts file entry (restart WSL2 it takes network settings from Windows OS)
  - `127.0.0.1 jobs-app.alphadev.local` (jobs-app)

### macOS

- Docker Desktop
  - make sure docker-compose is installed
  - also make sure hosts file are entries like in windows
    - path should be /private/etc/hosts (source: google)
    - https://www.nexcess.net/help/how-to-find-the-hosts-file-on-my-mac/

## Setup

After cloning jobs-app into your desired folder.

Go to root folder and run `docker-compose up -d`

When installation is done, go into the jobs-app container via WSL2 with

`docker exec -it jobs-app bash`. There install dependencies with

`composer install` or use

`docker-compose exec -w /var/www/jobs-app/ jobs-app composer install`

you can also run other commands in your container without entering it

`docker-compose exec -w /path/to/run/cmd desiredContainer any command`

When dependencies are installed try visiting

- `https://jobs-app.alphadev.local/`.

run tests
- `docker-compose exec -w /var/www/jobs-app/ jobs-app ./vendor/bin/phpunit ./tests`