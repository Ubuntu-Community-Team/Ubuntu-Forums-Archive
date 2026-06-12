---
title: "Can't get online"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by jasrog on 2006-06-14
I ran live cd ubuntu 6.06 but I cannot get online I get error right away and i made sure it was activated and still cannot get online. Please Help so I can get online...

---

### Post by neo_reloaded on 2006-06-14
What is/are the error message/messages?
any message in your dmesg?
any screenshots?
is the cable connected?
:)

---

### Post by Arnaud_B on 2006-06-14
if you are plugged (not wireless) check what is your interface name with ifconfig, this should be eth0, then make sure that /etc/network/interfaces look like that:
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet dhcp
if everything is ok until now do:
$route
if you see nothing do:
$sudo ifup eth0
and if it says that it is already configured do:
$sudo ifdown eth0
$sudo ifup eth0

Hope this helps,
Good luck!
A.

---

### Post by jasrog on 2006-06-14
error says cannot find server... my high speed cable connection works in windows....

---

### Post by neo_reloaded on 2006-06-15
Okay, so if you are connecting via ethernet cable,
1 - make sure your cable is connected,
2 - make sure your networking configuration is same as what you have on your windows
  - for example, i dont know if your ISP has given you private IP address etc. ( you need to call your service provider in that case - if you cannot set things up yourself)

---

