# Catalog-Deployment-Project


## Introduction

This is a baseline installation of a Linux server and preparation for hosting a web **Catalog** application. The server is secured from a number of attack vectors. A database server is installed and configured, and deployed with the same web applications onto it.

## Walkthrough

* The IP address and SSH port so the server:

  * IP address: 50.112.8.5

  * SSH Port: 2200


* The complete URL to hosted web application.

  * [Application URL](ttp://ec2-50-112-8-5.us-west-2.compute.amazonaws.com/)


* A summary of software installed and configuration changes made

  Get a server.
    1. Start a new Ubuntu Linux server instance on Amazon Lightsail. There are full details on setting up the Lightsail instance on the next page.
    2. Follow the instructions provided to SSH into the server.

  Secure the server.
    3. Update all currently installed packages.
    4. Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
    5. Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).
    
     * `sudo ufw allow 2200/tcp`
     * `sudo ufw allow 80/tcp`
     * `sudo ufw allow 123/udp`
     * `sudo ufw enable`

  Give grader access.
  

    6. Create a new user account named grader.
    
    
     * run command `sudo adduser grader`
     
    
    7. Give grader the permission to sudo.
    
    
     * add user to `/etc/sudoers.d/grader`
     
    
    8. Create an SSH key pair for grader using the ssh-keygen tool.

  Prepare to deploy the project.
  
    9. Configure the local timezone to UTC.
    
     * run command `tzdata`
    
    10. Install and configure Apache to serve a Python mod_wsgi application.
    11. Install and configure PostgreSQL:

  Do not allow remote connections
  
  Create a new database user named catalog that has limited permissions to the catalog application database.
  
    12. Install git.
     
     * original git repo is locacted in `https://github.com/yiclwh/Catalog-Server-Project.git`
     
     * change made for deployment had been checked into a seperate `Deployment` branch

  Deploy the Item Catalog project.
  
    13. Clone and setup the Item Catalog project from the Github repository you created earlier in this Nanodegree program.
    
    
     * add a `catalog.wsgi` file to run the web application over mod_wsgi
     
     * add a `catalog.conf` file to `/etc/apache2/sites-available/...` for hosting web app
     
     * install `postgresql`, create new database and user `catalog`
     
    
    14. Set it up in server so that it functions correctly when visiting the server’s IP address in a browser. Make sure that the .git directory is not publicly accessible via a browser!
    
    
     * add http://ec2-52-34-208-247.us-west-2.compute.amazonaws.com/ to authorized URI list in both google and facebook authentication OAuth setting portals
    
    
    
    
