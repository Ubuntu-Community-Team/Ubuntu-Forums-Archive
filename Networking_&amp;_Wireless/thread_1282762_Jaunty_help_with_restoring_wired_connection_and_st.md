---
title: "Jaunty: help with restoring wired connection and static ip setup"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by mangoes on 2009-10-04
Hi All,

Help please. I have a non-optimal solution to a broken wired connection.

Until yesterday I have been having NO problem with wired connection in Jaunty (64bit).  Then I mucked around with netgear usb wireless dongle  (it worked, but I then switched it off due to weak reception).  

After i did this, the wired connection would not work.  I don't think it's a problem with the modem/router or the isp, because other computers connected to the modem/router can still go online.

I managed to get a quick and dirty solution from this page
[http://technologyheaven.com/2009/03/21/workaround-for-wired-connection-problem-in-ubuntu-810-and-904/](http://technologyheaven.com/2009/03/21/workaround-for-wired-connection-problem-in-ubuntu-810-and-904/)

and created, via the network connection applets, a new wired connection, and select this instead of the 'ifupdown(eth0)'
But this brings other problem.

The problem is,  I have been using dynamic dns service in order to ssh into my machine from outside my home network.  So I have set up my linux box to have a static IP.   This had been working great thanks to the [help]("http://ubuntuforums.org/archive/index.php/t-722846.html") in this forum  (the setup I did for the static ip and port forwarding are in that link).  Now, the new quickndirty wired connection that I just created seems to ignore the static ip setup from the /etc/networking/interfaces and so the router just dishes out whatever ip in the dhcp range to my box.  So now all the port forwarding goes awry. I tried to set up the ipv4 setting to 'manual' and specify the ip address (via network connection manager)  but the 'apply' button is deactivated when I go down this route. Obviously not happy. 

So if someone knows how to bring back the wired connection without overwriting the static ip setup, it would be appreciated!!!

thanks in advance

ps:
using
netgear dg834g
ddclient
ubuntu 9.04

content of /etc/network/interfaces:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.0.5
gateway 192.168.0.1
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

---

### Post by Iowan on 2009-10-05
One option would be to set up the DHCP server (router?) to issue static lease to machine (if it is capable). 
Network Manager may balk at your manual settings because it no longer manages eth0. Try commenting out the settings in */etc/network/interfaces*, and restarting/rebooting. Then try editing via Network Manager. (If it still doesn't work, you can uncomment the static configuration lines).

---

