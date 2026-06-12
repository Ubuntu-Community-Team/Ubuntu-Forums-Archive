---
title: "Enabling Wireless Card"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by bradydehart on 2010-05-14
I just installed Ubuntu and I can't get the wireless Internet to work. I am brand new to Linux so please excuse my lack of knowledge.  I was able to do the network command search "sudo lshw -C network" and this is what it showed me

paola@paola-laptop:~$ sudo lshw -C network
[sudo] password for paola: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:6c:ee:07
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=129.123.227.118 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:61:04:25
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


What do I do from here? "Networking" is also not available under System -> Administration" I would really appreciate any help you all are willing to offer. Thank you!

---

### Post by cgroza on 2010-05-14
Go to system > administration > Hardware drivers and install the broadcom drivers.

---

