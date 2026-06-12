---
title: "Ubuntu 9.10, Belkin N+ USB Wireless (F5D8055 v2), no network"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Ortelius on 2010-01-24
I just installed Ubuntu 9.10 and my wireless network adapter doesn't work. It worked using my previous installation (Knoppix 6.2), so I suspect it isn't the hardware.

I have:
* Tried to use ndiswrapper to install the Windows drivers
* Built and installed the Linux drivers from the RALINK web site.

Neither option worked (assuming I did them correctly, which I may not have). 

lsusb can see the wireless adapter:

Bus 001 Device 002: 050d:825b Belkin Components

lshw -C network has this to say:

*-network
       description: Ethernet interface
       product: 82573V Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 03
       serial: 00:13:20:7a:95:86
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.0-5 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:4d100000-4d11ffff ioport:2000(size=32)
  *-network
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:21 memory:4d014000-4d017fff

Help, help!

---

