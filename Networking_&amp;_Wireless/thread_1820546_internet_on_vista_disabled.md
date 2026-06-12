---
title: "internet on vista disabled"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by yandawg on 2011-08-07
I recently installed ubuntu 11.04, using the dual boot option with windows vista. I have noticed that when I reboot with vista, it recognizes my wireless network, but is unable to connect to it. Internet works perfectly fine with ubuntu, just not with vista. How do I solve this?

I have tried disconnecting from the internet in ubuntu, and even uninstalling ubuntu, but it did not help. 

This is my output when I type “sudo lshw -C network“:

*-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:fddfe000-fddfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:00:5c:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=351.126 ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Iowan on 2011-08-07
Does it work if you boot into Vista from power-up (rather than a reboot)?
Sometimes the drivers don't reset properly...

---

### Post by yandawg on 2011-08-07
> **Iowan said:**
> Does it work if you boot into Vista from power-up (rather than a reboot)?
Sometimes the drivers don't reset properly...

Oh, wow that was it. I feel pretty dumb now o.O
lol thanks for the help

---

