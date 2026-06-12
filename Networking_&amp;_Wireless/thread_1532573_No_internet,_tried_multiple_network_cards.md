---
title: "No internet, tried multiple network cards"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by pittpaguy87 on 2010-07-16
Hi,

I have a Compaq and a gateway computer. I also have 2 network cards.
In both computers, I have tried the following distros of linux:
Ubuntu 10.4
Xubuntu 10.4
Ubuntu Server 10.4
Puppy Linux 5
Damn Small Linux

Computers:
---------------
Compaq 800 mhz
512 ram

Gateway 400 mhz
512 ram

Network Cards
--------------
Linksys 100tx

3Com Cyclone

In all combinations of computers, os, and network card, I have not been able to connect to the internet. Can someone give me some advice on where I should start and what I could try to connect. I have been stumbling around the forums with no luck to my problem. I can give you any output you would like.

Thanks in advance.

---

### Post by Iowan on 2010-07-16
On one of the *buntu's (dunno about puppy or DSL), check *ifconfig -a* to see if interface has an IP address. If not, **sudo lshw -C network** should show more information about the interface - driver, alias, etc...

---

