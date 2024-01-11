# Instructions to Install and Run eScriptorium on a Mac 

escriptorium is a web application that can be run on a local machine. This document describes how to install and run escriptorium on a Mac.

## Install Docker

- Follow this [link](https://docs.docker.com/desktop/install/mac-install/). Click on "Docker Desktop for Mac with Apple silicon" (in "About this Mac" it will show that you have an M chip) or "Docker Desktop for Mac with Intel chip" depending on your Mac.

- Double-click Docker.dmg to open the installer, then drag the Docker icon to the Applications folder.

- Double-click Docker.app (a whale with little containers on it) in the Applications folder to start Docker.

## Install HomeBrew

- Next you will need to install a program called [Homebrew](https://docs.brew.sh/Installation.)
- Open the Terminal application
- Paste the following command into the Terminal window and press Enter:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install Git

- With homebrew installed, you can now install git. In the Terminal window, paste the following command and press Enter:
```bash
brew install git
``` 


## Clone the eScriptorium Repository
From here, we'll be following the instructions from eScriptorium that can be found [here](https://gitlab.com/scripta/escriptorium/-/wikis/docker-install).

- In the Terminal window, navigate to the directory where you want to install eScriptorium. For example, if you want to install it in your Documents folder, type the following command and press Enter:
```bash
cd ~/Documents
```
`cd` stands for "change directory." 

Now enter the following command and press Enter:
```bash
git clone https://gitlab.com/scripta/escriptorium.git
```
This will create a folder called "escriptorium" in your Documents folder.
- Next enter the following command and press Enter:
```bash
cd escriptorium && cp variables.env_example variables.env  
```
This will create a file called "variables.env" in the escriptorium folder.

If you want to inspect the file you can type: 
```bash
open variables.env
```
This file contains settings for your local eScriptorium installation. You can change these settings if you want, but the default settings should work fine. Note that the default login information is username `admin` and password `admin`. 
```python
DJANGO_SU_NAME=admin
DJANGO_SU_EMAIL=admin@admin.com
DJANGO_SU_PASSWORD=admin
```

- You're now ready to install eScriptorium. Enter the following command and press Enter:
```bash
docker compose pull
```
This will download the latest version of eScriptorium.
- To start eScriptorium, enter the following command and press Enter:
```bash
docker compose up -d 
```
You will need to wait about five minutes for the application to startup and be ready to use.

- Next open your web browser and go to http://localhost:8000. You should see the eScriptorium login page. Enter the username and password from the variables.env file (default username is `admin` and default password is `admin`). You should now be logged in to eScriptorium.

- Note that you may need to export your image files and transcriptions from the escriptorium.pennds.org site. You can do this by going to the "Export" tab on the left side of the page. You can then import these files into your local eScriptorium installation by going to the "Import" tab on the left side of the page.

- You can now train models using your local laptop or desktop computer. 

- When you are done using eScriptorium, you can stop the application by entering the following command and pressing Enter:
```bash
docker compose down
```
or press the stop button in the Docker Desktop application.

- To restart it in the future, go to the Docker Desktop application and click on the "eScriptorium" container. Then click on the "Start" button. You can then go to http://localhost:8000 in your web browser to access eScriptorium. Alternatively you can enter the following command in the Terminal window and press Enter:
```bash
docker compose up -d
```

