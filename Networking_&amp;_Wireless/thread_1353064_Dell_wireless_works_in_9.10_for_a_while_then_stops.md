---
title: "Dell wireless works in 9.10 for a while then stops"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by kevinf on 2009-12-12
I am a newbie. I have been using 9.04 without any wireless problems. I am using a dual boot system with windows and wubi everytime I uptgrade to 9.10 wireless works for a couple of days then usually after an update it goes dead and I can not breathe life into any way. This is WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:1f:e1:3b:72:1f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.130 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:3f:ee:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:b4:7b:31:37:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
from one of the threads I was trying to understand. My computer is dell 1330. Could anyone help.

Thank you.

---

