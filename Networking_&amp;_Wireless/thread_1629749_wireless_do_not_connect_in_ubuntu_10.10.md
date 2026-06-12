---
title: "wireless do not connect in ubuntu 10.10"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by baraka607 on 2010-11-24
hi friends,
am using ubuntu 10.10 and wireless connection was working just fine untill today when i turn on my laptop and try to connect to a wireless connection with no success. i can see the wireless network list but when i try to connect it fails. Please help

---

### Post by Peter09 on 2010-11-24
We need the specification of your computer (especially the wireless card)
 
Do (in a terminal)
 
```
lshw -C network
```
 
and post the output.

---

### Post by Bucic on 2011-01-24
I hope you don't mind if I take over...

```
hg1@...:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
.
.
.
.
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0010000-d0011fff

```My network manager doesn't list my wireless controller but it may be due to this problem I'm still struggling with [http://ubuntuforums.org/showthread.php?t=1648409](http://ubuntuforums.org/showthread.php?t=1648409)

---

