---
title: "VNC Localhost???"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by kaelonlloyd on 2009-07-13
I am setting up a VNC remote desktop in my home and i want to be able to access my desktop pc from my laptop.
I've followed many tutorials and found out that i needed to disable advanced effects in appearance, but now another problems arises.
My desktop computer has an ip of 'localhost' so when i try to use VNC viewer by typing 'vncviewer localhost:5900' in the terminal all that happens is that i see my own laptop screen. My laptop has an ip 

Can anyone tell me how to access my desktop please???

Edit:
i can connect to my laptop in VNC from my desktop but not the other way round

---

### Post by cph05a on 2009-07-13
If you have compiz enabled, vino-server will not work. Try x11vnc:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

---

### Post by cosine352 on 2009-07-13
have a look at this one
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

works great for me. 

To get the ip address of your computer in local network 

> ifconfig | grep 'inet addr'

the first number will be your ip address. 

To access the machine from outside your local network you need to configure the router to forword the ssh port.

---

### Post by kaelonlloyd on 2009-07-13
> **cph05a said:**
> If you have compiz enabled, vino-server will not work. Try x11vnc:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

I've sorted that and got my desktop to connect to my laptop, but i can't connect from laptop to desktop because the desktop has an ip of localhost.
any ideas??

---

### Post by kaelonlloyd on 2009-07-13
> **cosine352 said:**
> have a look at this one
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

works great for me. 

To get the ip address of your computer in local network 



the first number will be your ip address. 

To access the machine from outside your local network you need to configure the router to forword the ssh port.


The ip address doesnt work, it gives an error that says its been refused, and i don't want this VNC to leave the home network.

---

### Post by doas777 on 2009-07-13
> **kaelonlloyd said:**
> I've sorted that and got my desktop to connect to my laptop, but i can't connect from laptop to desktop because the desktop has an ip of localhost.
any ideas??


your desktopp does not have an ip address of 'localhost'.
localhost is a symbolic constant name, which always refers to the local pc. 

if I type 'ping localhost' on any PC in the world, it will always ping the host that i am on. 
IP addresses are in the form of 192.168.1.1, and must be unique on your network.

go to the desktop, and open a terminal:
```
ifconfig
```
and look for your active network connection. then note the ip address displayed (will be similar to the one above). the IP must NOT start with '127' or '169'

then go back to the laptop, and run vncviewer, this time using the IP address instead of localhost.

---

### Post by kaelonlloyd on 2009-07-13
> **doas777 said:**
> your desktopp does not have an ip address of 'localhost'.
localhost is a symbolic constant name, which always refers to the local pc. 

if I type 'ping localhost' on any PC in the world, it will always ping the host that i am on. 
IP addresses are in the form of 192.168.1.1, and must be unique on your network.

go to the desktop, and open a terminal:
```
ifconfig
```
and look for your active network connection. then note the ip address displayed (will be similar to the one above). the IP must NOT start with '127' or '169'

then go back to the laptop, and run vncviewer, this time using the IP address instead of localhost.



the ip is on my desktop is 192.168.1.4, but when i type that i got the error 
vncviewer:ConnectToTcpAddr: connect : Connection refused 
Unable to connect to VNC server

---

### Post by doas777 on 2009-07-13
> **kaelonlloyd said:**
> the ip is on my desktop is 192.168.1.4, but when i type that i got the error 
vncviewer:ConnectToTcpAddr: connect : Connection refused 
Unable to connect to VNC server

have you enabled "remote desktop" in system -> preferences?

---

### Post by kaelonlloyd on 2009-07-13
> **doas777 said:**
> have you enabled "remote desktop" in system -> preferences?

Yes i have, that where it tells me that i have a ip 'local host', but on my laptop it tells me that i have an ip of 192.168.1.2 and a name of ubuntu.local

---

### Post by doas777 on 2009-07-13
> **kaelonlloyd said:**
> Yes i have, that where it tells me that i have a ip 'local host', but on my laptop it tells me that i have an ip of 192.168.1.2 and a name of ubuntu.local

well yeah it always gives the hostname as localhost.

are you saying the laptop is 192.168.1.4 and the desktop is 192.168.1.2?

if that is the case try this from the laptop. otherwise use the other IP. do not speficy the port number (:5900)
```
vinagre 192.168.1.2
```

---

### Post by cph05a on 2009-07-13
check your router settings. Maybe try forwarding tcp connections on port 5900 to your local ip address.

---

### Post by doas777 on 2009-07-13
> **cph05a said:**
> check your router settings. Maybe try forwarding tcp connections on port 5900 to your local ip address.

are you connecting from a remote PC over the Internet? if so you want to tunnel over ssh. if you forward the port, anyone could get in and start using your PC.

---

### Post by kaelonlloyd on 2009-07-13
> **doas777 said:**
> are you connecting from a remote PC over the Internet? if so you want to tunnel over ssh. if you forward the port, anyone could get in and start using your PC.

I'm not using it outside my network(router) and i've restarted my desktop just now an it now shows and ip and a name rather than localhost, but i still can't connect

---

### Post by doas777 on 2009-07-13
if you are on the desktop, are you able to connect to the service locally?

also do you use a firewall configuration tool like gufw or firestarter?

---

### Post by kaelonlloyd on 2009-07-13
> **doas777 said:**
> if you are on the desktop, are you able to connect to the service locally?

also do you use a firewall configuration tool like gufw or firestarter?

NO firewalls that are turned on, my router firewall isn't a problem i don't think because i can control my laptop from my desktop.

---

### Post by doas777 on 2009-07-13
> **kaelonlloyd said:**
> NO firewalls that are turned on, my router firewall isn't a problem i don't think because i can control my laptop from my desktop.

well, ubuntu has a firewall build in (called IPTables), but it doesn't do much unless you configure it. that was kinda the gist of my question. usually when you install/enable a service it configures IPTables to allow traffic on the specified port, but it is possible that this mechanism failed.

just to confirm, you can ping both ways, right? can you access the desktops vnc locally?
check your kernel log on the desktop to see if there are any messages about IPTables blocking traffic. do you have any other services running on the desktop (samba, ssh, etc)?

---

### Post by kaelonlloyd on 2009-07-13
> **doas777 said:**
> well, ubuntu has a firewall build in (called IPTables), but it doesn't do much unless you configure it. that was kinda the gist of my question. usually when you install/enable a service it configures IPTables to allow traffic on the specified port, but it is possible that this mechanism failed.

just to confirm, you can ping both ways, right? can you access the desktops vnc locally?
check your kernel log on the desktop to see if there are any messages about IPTables blocking traffic. do you have any other services running on the desktop (samba, ssh, etc)?

Ping is working Both ways
Yes i can access VNC locally
There is no kernal log on the desktop
And im running nothing else that would use the internet.

---

### Post by doas777 on 2009-07-13
> **kaelonlloyd said:**
> Ping is working Both ways
Yes i can access VNC locally
There is no kernal log on the desktop
And im running nothing else that would use the internet.

you can view your kernel log with the Log File Viewer in System->Administration

---

