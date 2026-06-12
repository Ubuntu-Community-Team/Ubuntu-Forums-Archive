---
title: "My Network Setting"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by Last User on 2009-05-25
Hi all, I'm new to Ubuntu.
I'm trying to set up my network connection on my new Ubuntu but I'm stuck.


This is my TCP/IP Setting on XP.

IP Address  : 171.191.38.10
Subnet Mask : 255.255.0.0
Gateway     : 10.106.10.254

DNS
Preferred   : 10.3.3.77
Alternate   : 10.9.9.77

Advance TCP/IP Settings

IP Address        Subnet Mask
171.191.38.10        255.255.255.0
10.106.10.253        255.255.255.252

Is there any way that I can set that up on Ubuntu? I'm trying several IP combination, but it still won't connect to the internet. Or is there a tool in Ubuntu that can import my connection setting from XP. By the way, I'm using Ubuntu 9.0.4

Thanks for answering.

---

### Post by W03L on 2009-05-25
> **Last User said:**
> Hi all, I'm new to Ubuntu.
I'm trying to set up my network connection on my new Ubuntu but I'm stuck.


This is my TCP/IP Setting on XP.

IP Address  : 171.191.38.10
Subnet Mask : 255.255.0.0
Gateway     : 10.106.10.254

DNS
Preferred   : 10.3.3.77
Alternate   : 10.9.9.77

Advance TCP/IP Settings

IP Address        Subnet Mask
171.191.38.10        255.255.255.0
10.106.10.253        255.255.255.252

Is there any way that I can set that up on Ubuntu? I'm trying several IP combination, but it still won't connect to the internet. Or is there a tool in Ubuntu that can import my connection setting from XP. By the way, I'm using Ubuntu 9.0.4

Thanks for answering.
you need edit /etc/network/interfaces:
#
auto lo
iface lo inet loopback
#
iface eth0 inet static
address 171.191.38.10
netmask 255.255.0.0
gateway 10.106.10.254
auto eth0
----------------------------
than edit or create /etc/resolv.conf:
nameserver 10.3.3.77
nameserver 10.9.9.77
----------------------------
and edit /ect/hosts:
127.0.0.1 localhost nameOfYourPC

than /etc/init.d/networking restart
;)

---

### Post by Last User on 2009-05-25
Thanks answering W0EL, I will try it. Is it required to restart the system after new setting applied?

---

### Post by Iowan on 2009-05-25
A couple more options... You should also be able to enter the IPv4 information into Network Manager applet. If so, you will *probably* need to restart Network Manager (/etc/init.d/NetworkManager restart).
 Typically, 127.0.0.1 is left as localhost, and the hostname is assigned to 127.0.1.1 in /etc/hosts.
Sometimes restarting the system is about as easy as restarting the service you modified.

---

### Post by Last User on 2009-05-25
Thanks all. The first options works for me.
Mod can close the thread now ;)
Problem SOLVED :D

---

