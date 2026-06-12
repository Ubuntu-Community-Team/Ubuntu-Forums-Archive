---
title: "Randomly changes from Static IP to DHCP"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by zerek on 2011-12-23
Ubuntu server 11.10:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.100
network 10.0.0.0
broadcast 10.0.0.255
netmask 255.255.255.0
gateway 10.0.0.1


/etc/init.d/networking restart

By using a restart IP goes back to 10.0.0.100, but after a few hours it randomly go DHCP and give out a new IP.
Router IP pool from is set from 10.0.0.1 to 200 and noone else uses this IP as far as I know.
This computer is connected at to a (wireless) range extender via ethernet.
Router ---wifi--- Range extender-Computer


How do I prevent it from randomly changing IP addresses all the time?

---

### Post by zerek on 2011-12-23
[http://ubuntuforums.org/showthread.php?t=1898637](http://ubuntuforums.org/showthread.php?t=1898637)

see that others got the same problem, ill check that topic

---

