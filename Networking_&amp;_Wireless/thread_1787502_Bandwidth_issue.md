---
title: "Bandwidth issue"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by electronictim on 2011-06-21
Hi there.

The problem:  recent install of Ubuntu 11.04, but problems with very slow internet connection.  Have disabled ipv6 (in network settings and firefox) and also disabled power management of wireless adaptor.  Situation is improved, but not great.  Still significantly slower than windows machines and macs running through the same router (all using wireless).  Any way that I can change the order of priority for bandwidth usage at the router, or any other suggestions that might improve matters?

Thanks.

---

### Post by nbound on 2011-06-21
plz post output of **lshw -C network**

---

### Post by electronictim on 2011-06-21
```
root@Huckleberry:/home/ashifa#  lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:10:dc:e3:d9:80
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:ec00(size=256) memory:e4524000-e4524fff memory:40020000-4003ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:1
       logical name: wlan0
       serial: 00:11:50:c2:3b:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-8-generic firmware=1.7 ip=192.168.0.3 link=yes multicast=yes wireless=IEEE 802.11bg
root@Huckleberry:/home/ashifa# 

```

---

### Post by electronictim on 2011-06-21
Bump.  (Please help!)

---

