---
title: "Does this (terminal output) mean I haven't got Wireless dongle drivers installed?"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by Gamer Boy on 2013-01-12
martin@martin:~$ ifconfig >> ~/abs-wireless.txt
martin@martin:~$ sudo lshw -C network
[sudo] password for martin: 
Sorry, try again.
[sudo] password for martin: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5782 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 03
       serial: 00:0e:7f:66:38:7e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5782-v3.13 ip=192.168.1.36 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:20 memory:fc500000-fc50ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan1
       serial: 00:0b:81:87:d0:79
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-35-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
martin@martin:~$ ^C
martin@martin:~$

---

### Post by ahallubuntu on 2013-01-12
Yes, you have a driver installed, but it also means you are using a dongle with a Realtek 8192CU chipset - which doesn't work out-of-the-box in Ubuntu 12.04 LTS or in 12.10.  It KIND of works but not reliably.  Sometimes it connects, sometimes not. You'll want to build the latest driver from Realtek instead.

Follow these instructions carefully (make sure you get "RTL8192CU" from Realtek's website - version "3.4.4_4749" at this moment):

[http://ubuntuforums.org/showpost.php?p=12318056&postcount=2](http://ubuntuforums.org/showpost.php?p=12318056&postcount=2)

Don't forget the blacklisting or adding the new module name.

---

### Post by Gamer Boy on 2013-01-12
That worked - 
[http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/](http://thatguruguy.wordpress.com/2012/09/04/working-rtl8188cus-in-ubuntu-12-04/)

Thanks!

PE

---

