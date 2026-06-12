---
title: "SIOCDELRT: No such process"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by tanxs001 on 2012-03-12
/etc/networking/interfaces&#65306;
  4 auto eth0
  5 iface eth0 inet static
  6 address 18.8.9.96
  7 netmask 255.255.255.0
  8 gateway 18.8.0.1

when run&#65306; sudo /etc/init.d/networking restart

it wil be error&#65306;
SIOCADDRT: No such process
Failed to bring up eth0.

I find that the IP address &  default gateway are on separate networks. it will cause this problem, I search much but it don't have any solution. 

[http://ubuntuforums.org/showthread.php?t=995043&highlight=SIOCADDRT%3A+process](http://ubuntuforums.org/showthread.php?t=995043&highlight=SIOCADDRT%3A+process)

on other article it provide a method that add gateway on /etc/rc.local, but i can't work also. 
[https://bbs.archlinux.org/viewtopic.php?pid=289404](https://bbs.archlinux.org/viewtopic.php?pid=289404)

thanks for your help, my ip address and gateway is assigned by company&#65292; can't be change it.

---

### Post by tanxs001 on 2012-03-13
anybody&#65311;

---

