# Dependencies

 * Docker - https://docs.docker.com/install/
 * Docker compose - https://docs.docker.com/compose/install/

# Getting started

```bash
docker-compose up
```

On the first run, this will start downloading the base images and will start the server in the attached mode - with the terminal and OpenLDAP startup logs hooked on.

For more options starting up, please see https://docs.docker.com/compose/reference/up/.


### Managing Docker containers and images

For those unfamiliar with Docker here are a few useful commands:

```bash
# SSH into a running container
docker exec -i -t [<CONTAINER-ID>|<CONTAINER-NAME>] /bin/bash

# List running containers
docker ps

# List all containers
docker ps -a

# Remove container
docker rm [<CONTAINER-ID>|<CONTAINER-NAME>]

# List local main images
docker images

# List local images
docker images -a

# Remove image
docker rmi <IMAGE-ID>

```

# Connections

Using ldap protocol:

* **Server** - ldap://localhost:389
* **Bind DN** - `cn=admin,dc=example,dc=org`
* **Bind Password** - `admin`

Using SSL:

* **Server** - ldaps://localhost:636
* **Bind DN** - `cn=admin,dc=example,dc=org`
* **Bind Password** - `admin`

> **Note**: If you plan to use SSL, change the **domainname** and **hostname** parameters on the `docker-compose.yml` file accordingly. For localhost tests you can edit your `/etc/hosts` file like so:

```bash
# binds the hostname ldap.example.org to the loopback interface
127.0.0.1 ldap.example.org
```


# Sample data

The directory is initially loaded with the sample data contained in the file `ldap/directory.ldif`.

That's the structure you'll find:

* dc=example,dc=org
    * cn=**admin**
    * ou=**Groups**
        * cn=**Administrator**
        * cn=**Developers**
    * ou=**People**
        * cn=**leonardo**
        * cn=**marpontes**
        * cn=**zach**

# More options

This repository only configures [osixia/docker-openldap](https://github.com/osixia/docker-openldap) by using Docker Compose. To see all the options available please refer to the original repository linked above.

# Managing the directory

An easy way to manage the objects on your running directory is by using [Apache Directory Studio™](http://directory.apache.org/studio/). 

It might be useful to:

* Test connections;
* Test searches;
* View and change objects.