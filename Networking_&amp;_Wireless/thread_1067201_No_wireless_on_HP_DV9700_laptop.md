---
title: "No wireless on HP DV9700 laptop"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by VMysteriis on 2009-02-11
Just did an out of box install of ubuntu 8.10 (64bit) on my dv9700 and I'm having trouble with my wireless.

here's the result of the lshw -C network (sorry have to type it since I'm on another comp)

*-network DISABLED
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:lb:24:fa:3a:bc
capacity: 100MB/S
width: 32bits
clock: 66MHz
capabilities: pm msi ht bus master cap list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0
*network DISABLED
description: Ethernet interface
physical id:1
logical name: pan0
serial: 32:34:a1:e6:92:c0
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by FishRCynic on 2009-02-11
try here

[http://ubuntuforums.org/showthread.php?t=984605&highlight=DV9700](http://ubuntuforums.org/showthread.php?t=984605&highlight=DV9700)

---

