---
title: "gutsy upgrade - lircd broken - no mceusb2"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by dc2447 on 2008-01-10
Upgrded to gutsy now lircd is dead


irw shows connection refused and there is no /etc/lirc[0] device


reconfigured lirc and got this


> root@mac-mini:/etc# dpkg-reconfigure lirc
Stopping lirc daemon: lircmd lircd.
 * Reloading kernel event manager...                                                                                   [ OK ] 
Setting up modutils file
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.
root@mac-mini:/etc# 
root@mac-mini:/etc# 
root@mac-mini:/etc# 
root@mac-mini:/etc# apt-get install  lirc-modules-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lirc-modules-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
root@mac-mini:/etc# irw
connect: Connection refused
root@mac-mini:/etc# lsusb -v | grep -i philips
Bus 003 Device 005: ID 0471:0815 Philips 
  idVendor           0x0471 Philips
  iManufacturer           1 Philips


---

### Post by dc2447 on 2008-01-10
Gutsy had decided I wanted a server kernel - reverting to generic fixed this issue

---

