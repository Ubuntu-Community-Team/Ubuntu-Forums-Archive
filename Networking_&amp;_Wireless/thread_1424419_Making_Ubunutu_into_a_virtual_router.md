---
title: "Making Ubunutu into a virtual router"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by mangrovecrab on 2010-03-07
So for a final in my networking class I was asked to do this using any resources online. ;)

Basically I'm wondering if there are any easy to follow tutorials or tools available to use a fresh virtual install of Ubuntu (or any other distribution) as a virtual router capable of being able to filter traffic from a connected client through a firewall. I've been trying a few hits on which came up googling but I've run into a some walls following them; any help would be appreciated. Thanks. :)

---

### Post by Charly85551 on 2010-03-09
Interesting task! Try the following: Ubuntu Server version probably easier but not mandatory. On a PC with 2 network ports (eth0 and eth1 for example) you assign one with internet access (with PPPoE for example, but a standard router is even easier for the demo) and the other for the internal network with a static IP-address of something like 192.168.1.1 as the gateway. Then install proxy-software with *squid* (standard version on Ubuntu download site) for the router function and any firewall software like* ipkungfu* which works with iptables. Even DHCP-server can be added but not mandatory. The only tricky thing is the editing of the squid.conf file since you need to define what is allowed and what not. However there are many commenting lines (> 4000!!) to guide you.
hope it works for you. Good luck
cheers
Charly85551

---

