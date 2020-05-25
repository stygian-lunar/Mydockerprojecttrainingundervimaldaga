Docker Project: Launching ownCloud via Docker Compose Overview:-

This project is based on Docker technology and is created by integrating the technologies Linux RHEL8 (RedHat 8), Python3, Docker, MySQL etc. Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. OwnCloud is a self-hosted file sync and share server. It’s functionally similar to as DropBox, Google Drive etc. This gives us access to our data (files, calendars, contacts, mails etc) through a web interface, across all the devices.

Here, I have deployed the ownCloud architecture inside a docker container and have linked it to MySQL database which is also been deployed in another container. Using Docker Containers, it will be deployed using minimal RAM and in minimal time (few seconds).

Both the containers are attached to persistent storage (volume) which has been created to ensure that there is no data loss in case of any system failure (crashing of containers or server i.e. been hosted on docker container due to load).

In this project, docker-compose is used through which we can set all environment in one single click by using one single file within a second.

No rush. No hustles !!

Built with:

Oracle Virtual Box RedHat Linux RHEL8 Docker OwnCloud MYSQl Project Flow:

Download and install Docker Start Docker Services Docker Compose installation (as it doesn’t come pre-installed with Docker) Create Containers for the server and database. Create Docker volume for persistent storage. This step is required because docker containers are by default ephermal in nature which leads to data loss in case of crash or system failure. Pull images from DockerHub (the public repository of Docker). Set up ownCloud self-hosted file sync and share server. Set Up MySQl Database. Linked both the conatiners Launching containers with Docker_compose via command: docker -compose up Requirements/Installation:

Make sure you have the latest versions of Docker and Docker Compose installed on your machine. If not then follow below commands_

sudo apt-get update sudo apt-get remove docker docker-en

gine docker.io sudo apt install docker.io

Docker Installation on RedHat:

Configure yum by adding docker.repo and dvd.repo inside the “/etc/yum.repos.d” for local installation using https://download.docker.com/linux/redhat/docker-ce.repo

Start Docker:

sudo systemctl start docker sudo systemctl enable docker

Install Docker Compose:

sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s-uname -m` -o /usr/local/bin/docker-compose sudo chmod +x /usr/local/bin/docker-compose

Download the Required Images:

Downloading the required docker image for ownCloud and MySQL from https://hub.docker.com using below commands: docker pull owncloud:latest docker pull mysql:5.7

Using Docker Compose:

Starting containers

• docker-compose start

Stopping containers

• docker-compose stop

Volumes:

Persistent Storage: All our data will be permanent if we attach a persistent volume to the containers where OwnCloud and MySQL deployed and stores data. This ensures the data will remain permanent if any of the container crashes or terminates. OwnCloud uses database server. So, defining database container and the Database (MySQL in my project) connected as back-end for ownCloud to host on web-server.

docker -d -i -t -e OWN_DB_HOST=(my_database_name) OWN_ROOT_PASSWORD=(your_password) -e OWN_ROOT_USER=(username) -e OWN_PASSWORD=(your_password) -e OWN_DATABASE= (any_database_name) -v name -p 8081:80 --name ownos --link dbos owncloud:latest

Usage:

Open a terminal and cd to the folder in which docker-compose.yml is saved and run the below command_

docker-compose up

Then we can access the ownCloud server website, built under Docker

yml file for the project https://github.com/stygian-lunar/Mydockerprojecttrainingundervimaldaga/blob/master/mydockerproject.yml
