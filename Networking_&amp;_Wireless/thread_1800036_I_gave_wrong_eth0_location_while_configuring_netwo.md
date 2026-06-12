---
title: "I gave wrong eth0 location while configuring network. How do I correct?"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by arroy_0209 on 2011-07-08
I tried to configure the network connection in Ubuntu 10.04 LTS by these commands (for ADSL modem):
sudo ifconfig eth0 19.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth0
sudo route add default gw 192.168.1.1
sudo pppoeconf
and following the instructions. Notice that by mistake I have written 19.168.1.1 after eth0 where I should have written 192. May be because of this the network configuration has suffered, though it is working. I can no longer load the page [http://192.168.1.1](http://192.168.1.1) in mozilla firefox. How do I correct this mistake?

---

### Post by Iowan on 2011-07-08
I presume you've tried re-entering the command with the proper address?
What are the results of **ifconfig -a**? 
The (wrong) changes hold after reboot?

---

