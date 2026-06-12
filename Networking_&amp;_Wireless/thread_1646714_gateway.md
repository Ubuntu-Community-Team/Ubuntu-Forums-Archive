---
title: "gateway"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by sureshk89 on 2010-12-16
Hi
I am new to ubuntu.I need some help for making my eth0 as default gateway.
eth0 to internet
eth1 internal lan

When i start everytime i need to disable eth1 to get access from internet.When both lans are active its not connecting to internet.

i tried vi /etc/network/interfaces
""auto lo
iface lo inet loopback""

How to edit this.

eth0                                                                eth1
192.168.1.60                                                 192.168.0.1
255.255.255.0                                               255.255.255.0
192.168.1.1                                                   192.168.0.1

Should i change the interfaces file.
Thanks 
Suresh

---

