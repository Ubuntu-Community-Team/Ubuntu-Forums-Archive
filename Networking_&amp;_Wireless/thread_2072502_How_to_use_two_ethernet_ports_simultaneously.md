---
title: "How to use two ethernet ports simultaneously"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by dsurfer21 on 2012-10-17
Hello, I posted the information below in another section but I wasn't sure if it needed to go in the generic help section.

 
I am running ubuntu 12.04.  I have a desktop that has two ethernet  cards.  I would like to use one ethernet port (eth 1) for SSH  connections or connecting to a LAN to access the internet.  The other  ethernet port is to use an ethernet IP camera.

I am having an issue where I can use SSH or the LAN on eth1 when I have  the camera disconnected from eth0.  I can also use the camera on eth0  only when I am disconnected on eth1.

How can I run them simultaneously?

I am not very knowledgeable with networking but the /etc/network/interfaces is setup like:
[FONT=monospace]
[/FONT]    auto eth0     
iface eth0 inet static         
address 192.168.0.92         
netmask 255.255.255.0         
gateway 192.168.0.254
    
auto eth1     
iface eth0 inet static         
address 192.168.0.77         
netmask 255.255.255.0         
gateway 192.168.0.254


The IP address of the camera is 192.168.0.90.  I'm not sure how to set  up the gateways.  Could that be the problem? I would like to use static  IP addresses. When I run ifconfig eth0 and eth1 show up properly with  the ip addresses that I specified above.

I'm hoping there is a solution.  I modified the grub file so that I can  boot up right into a terminal.  I then use sudo service lightdm when I  want to run ubuntu desktop.  I'm hoping I can use both ethernet ports  simultaneously right at the command prompt when it boots up, and also  when I start ubuntu desktop.

Thanks.

---

### Post by nothingspecial on 2012-10-18
*Thread moved to **Networking & Wireless**.*

---

