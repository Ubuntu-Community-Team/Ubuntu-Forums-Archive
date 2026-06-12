---
title: "wired network problem / upload problem."
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by kbish on 2009-12-21
Sorry for my English. 

I run Ubuntu 9.10 in my laptop HP6710s and have problem with wired network. I can't upload big files and test upload speed because wired network stop working after some second after speed test(file upload) has run. 
 Ping looks like this: 
 Ping: Sendmsg: No Buffer Space Available 
===============
kbish@epsilon:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
===============
kbish@kbish:~$  lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:7d:ae:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:e4100000-e4100fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:18:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:5a:0a:86
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v3.04 ip=85.254.44.250 latency=0 multicast=yes
       resources: irq:31 memory:e4000000-e400ffff
================

---

### Post by shredder12 on 2009-12-22
After searching about this ping send msg problem I found out a few work arounds...
One of them was fixed by setting a high value to /proc/sys/net/core/wmem_max.. it was [here]("http://www.linuxquestions.org/questions/linux-networking-3/sendmsg-no-buffer-space-available-334631/") 
and in other cases the problem was with the interrupt handling.. some sort of shared interrupt requests..  The solution was not specific but was related to some bios config..
I am not sure but I think that the second case could be the problem for you.

---

