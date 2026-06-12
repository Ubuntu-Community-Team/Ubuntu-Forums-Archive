---
title: "problems with airmon?"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2010-02-28
Hi i,m just starting to use aircrack, I have looked on google & think I have found my 1st problem. When I run airmon i get the following I cant switch to monitor mode


[HTML]-e 
usage: /usr/sbin/airmon <start|stop> <interface> [channel]

-e Interface    Chipset        Driver

wlan0        Unknown        Unknown
[/HTML]It looks like the chipset / driver has a problem,

This is result of lshw -C network it shows driver b43 

[HTML] *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:36:48:05:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=10.42.43.11 latency=173 maxlatency=11 mingnt=52 multicast=yes
       resources: irq:19 ioport:2000(size=256) memory:e2003000-e2003fff memory:28000000-2801ffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2004000-e2005fff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:69:4a:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
[/HTML]or is there something else I should be doing,
can supply any other info if need be
Thanks in advance

---

### Post by spiky001 on 2010-02-28
bump

---

### Post by spiky001 on 2010-03-01
anyone

---

### Post by realzippy on 2010-03-01
try nubuntu liveCD.it comes with patched drivers (monitor mode)..

[http://nubuntu.org/downloads/click.php?id=9](http://nubuntu.org/downloads/click.php?id=9)

---

### Post by spiky001 on 2010-03-01
ok i.ll give it a try ta

---

