---
title: "Missing Wireless access point"
date: 2012-09-01
forum: Networking &amp; Wireless
---

### Post by nvcnvn on 2012-09-01
I have an:

Ubuntu 12.04 with proprietary Boardcom STA Wireless driver installed
BCM43224 802.11a/b/g/n wireless card
TP-LINK TD-W8101G 54Mbps Wireless ADSL2+ Modem Router
Yesterday before I went to sleep, I still connect to my wireless access point, this morning when I start my laptop I don't see it in the list - there are some neighbors listed but not mine.
The WLAN is green, with my old Nokia E72, I still see my access point with 100% signal. I have tried to restart my laptop and turn the firmware off/on by the switch but no help. I have read the WirelessTroubleShootingGuide but I can do anything. Here is some of my card info:
> *-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: c0:cb:38:06:5d:53
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: f0:4d:a2:42:ab:e4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:5000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff memory:f0420000-f043ffff

---

