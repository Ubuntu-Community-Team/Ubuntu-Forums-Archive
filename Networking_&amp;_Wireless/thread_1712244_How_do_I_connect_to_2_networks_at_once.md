---
title: "How do I connect to 2 networks at once?"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by CLCressman on 2011-03-22
I have an ethernet card connected to my LAN and a USB cell modem internet connection. I am running ubuntu 10.10. The problem is this: I can use either network, but only if I am connected to one of them. If I connect to both at the same time my speed drops to zero. If I disconnect one, the other starts working. I have done a lot of searching and reading, but it looks like I don't know how to find what I am looking for.

My LAN was setup as 3 WinXP computers peer to peer. One of those computers was replaced by this one that I am having trouble with (computer A). Another one was replaced by one that is not yet on the network (computer C). Computer B dual boots Win XP and ubuntu 10.4. Mostly it runs xp for Quickbooks and BobCAD, also it is connected to the printer. My router is setup for DHCP.

I have done a little networking, mostly with Windows.

Thanks in advance.

---

### Post by Fire_Chief on 2011-03-22
So as a rule, a computer can only have 1 gateway to get to the Internet (aka everything not local). To maintain this setup with simplicity, NetworkManager only allows connections to one network at a time. You can get around this though to be connected to your local network strictly for communication with the other PCs AND be connected to your USB cell modem for all things Internet (read non-local).

You will need to set a static IP address for your LAN side connection. As a good practice, pick an IP in your subnet that is not in the DHCP range (if you have DHCP setup).

Go ahead and have your USB cell modem connected through NetworkManager. 
For the sake of example, let's say your LAN is using a 192.168.1.0 network with a subnet mask of 255.255.255.0. And we'll assume that DHCP (on a router)offers addresses from 192.168.1.1 to 192.168.1.100 with the router having 192.168.1.254.
Open a terminal window and type```
sudo ifconfig eth0 192.168.1.101 netmask 255.255.255.0 broadcast 192.168.1.255
sudo ifconfig eth0 up
```
If you got no errors, you should now be able to ping the other workstations on your LAN by their IP addresses. This is not a permanent configuration and will be lost when you either reboot or have NetworkManager try to connect to the LAN interface instead of the USB modem. To make the assignment permanent, have a look at this site [http://codesnippets.joyent.com/posts/show/319]("http://codesnippets.joyent.com/posts/show/319") 
IMPORTANT! If you follow the setup on the site above, do NOT include the gateway line in your setup. Ubuntu will get confused and you will have problems getting to the Internet.

Cheers!

---

### Post by BkkBonanza on 2011-03-22
You can have more than one gateway and various load balancing methods. But you have to implement some advanced techniques and cannot do it with NetworkManager (which is a simplified solution for simple network connection, and even a bit brain dead at that).

---

