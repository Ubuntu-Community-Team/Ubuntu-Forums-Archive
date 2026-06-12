---
title: "Broadcom WPC54GS Wireless Card Installation"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by cococrispgarren on 2009-07-13
I'm trying to install my Linksys Broadcom WPC54GS Wireless Card in 9.04 and having absolutely no luck. I have very little idea as far as what I'm doing, so any help would be greatly appreciated.

---

### Post by superprash2003 on 2009-07-14
post output of **lshw -C network** from the ubuntu termianl

---

### Post by cococrispgarren on 2009-07-14
Output from lshw -C network:
```
*-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:84:4f:4c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.107 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes

```

---

