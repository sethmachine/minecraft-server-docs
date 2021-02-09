# minecraft-server-docs
This is a guide for setting up a custom Minecraft forge server at home that can be made public and thus accessible to anyone with a compatabile Minecraft client.  The guide assumes the machine is running on a local home network (and thus physically accessible), though once this setup is complete, all management can be done remotely.  

## Prerequisites

* A modern machine to run the server (the "host"), should have at least 4 GB of RAM dedicated to the server process.
* Remote access to the machine to simplify management, i.e. ssh or Remote Desktop


## Set up remote access
Enable remote access will simplify future administration through simple terminal commands.  This assumes the machine has ssh enabled, which is available on Linux and Mac operating systems.  

* On Mac, enable ssh
* On Windows, enable remote desktop or install an ssh server



## Install Java 8 Development Kit (JDK)



## Port Forwarding for host machine
The Minecraft server will run on a specific port.  The default is 25565, but other values can be used.  For at home server, this port needs to be "forwarded" for both UDP and TCP protocols.  

1. Find the internal IP of the host machine.  On Windows run `ipconfig` and for Mac: https://apple.stackexchange.com/questions/20547/how-do-i-find-my-ip-address-from-the-command-line.  
1.  Access the at home router in a web browser, e.g. navigate to "192.168.1.1".  The actual at home IP address may be different.  
1. Find a tab or menu that includes "Port forwarding", "Firewall", or it may be under "Advanced".  
1. Create a new port forwarding rule from any incoming port to the Minecraft port 25565, for both TCP and UDP.  
1. Apply this rule the internal IP address of the host machine found in the first step.  
E.g. it might look like `Any -> 25565 TCP`, `Any -> 25565 UDP`


## Disable Minecraft authentication
* Set `online-mode=False` in the `server.properties` file.  

## Test connection
Go to https://mcsrvstat.us.  Enter the external IP address followed by a colon and the port number.  

## Host machine set up
* Enable passwordless ssh: http://www.linuxproblem.org/art_9.html
* Enable passwordless sudo: https://serverfault.com/questions/160581/how-to-setup-passwordless-sudo-on-linux
* Set the internal IP to a useful name for easy access via the `/etc/hosts` file, e.g. 

```
<INTERNAL-IP-ADDRESS> minecraft-server
```

## Setup server daemon
This allows for the server to start up automatically when the host machine restarts.

* For Mac: https://minecraft.gamepedia.com/Tutorials/Create_a_Mac_OS_X_startup_daemon
