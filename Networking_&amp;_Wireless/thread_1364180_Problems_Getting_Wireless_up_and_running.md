---
title: "Problems Getting Wireless up and running"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by ravosava on 2009-12-25
With every release since I've installed Ubuntu on my HP laptop, starting at 8.04, I've never been able to get wireless up and running. 

I believed with 9.10 it would change, that I would finally be able to use wireless, but after scouring the internet for tutorials, troubleshooting, fixes, and what have you, I've had no success.

I have an Atheros AR928X wireless card. 


Also, this is the output I get when I "sudo lshw -c network"


*-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e2:cd:50:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d1200000-d120ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:99:b5:dd
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d102ffff(prefetchable)


What am I doing wrong?

---

