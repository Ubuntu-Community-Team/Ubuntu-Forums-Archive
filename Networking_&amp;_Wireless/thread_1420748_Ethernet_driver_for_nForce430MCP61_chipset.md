---
title: "Ethernet driver for nForce430/MCP61 chipset?"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by bwallum on 2010-03-03
Hi

I have a motherboard with a MCP61 chipset running 64bit 9.10.

Is there an appropriate driver to get the onboard ethernet adapter working? I can get connection using an ethernet adapter on a pci card (Intel based).

ON BOARD LAN
description: Ethernet interface
product: MCP61 Ethernet
vendor: nVidia Corporation
physical id: 7
bus info: pci@0000:00:07.0
logical name: eth2
version: a2
serial: this is a mac address removed for security
size: 100000000
capacity: 100000000
width: 32 bits
clock: 66MHz
capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=half latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
resources: irq:27 memory:fe02d000-fe02dfff ioport:ec00(size='8')

ON CARD LAN
description: Ethernet interface
product: 82557/8/9/0/1 Ethernet Pro 100
vendor: Intel Corporation
physical id: 6
bus info: pci@0000:01:06.0
logical name: eth3
version: 08
serial: this is a mac address removed for security
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
resources: irq:18 memory:fdaff000-fdafffff ioport:bc00(size=64) memory:fd900000-fd9fffff memory:fdf00000-fdffffff(prefetchable)

EDIT
Also found this returned using```
sudo pcnet-diag
```Index #1: Found a AMD PCnet/PCI series adapter at 0.
This chip has not been assigned a valid IRQ, and will not function.
 This must be fixed in the PCI BIOS setup.  The device driver has no way
 of changing the PCI IRQ settings.
 See  [http://www.scyld.com/expert/irq-conflict.html](http://www.scyld.com/expert/irq-conflict.html)  for more information.
This chip has not been assigned a valid I/O address, and will not function.
 If you have warm-booted from another operating system, a complete 
 shut-down and power cycle may restore the card to normal operation.

---

