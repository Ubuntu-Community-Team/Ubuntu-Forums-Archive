---
title: "Problem with wireless conection"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by Lazaa on 2012-10-23
Hi, I have got ubuntu 12.04 and I've got one problem. I can't join to any wifi site.I found that I've got "BCM4313 802.11b/g/n Wireless LAN Controller". I'm was searching for some solution,but I don't work in linux for a long time. So if anyone would like to help I would be very grateful.

lspci | grep work

```
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```sudo lshw -C network

```
*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:43:82:a2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=sb ip=147.232.182.181 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff
  *-network DISABLED
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c0:18:85:80:70:ec
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:b3500000-b3503fff
```

---

