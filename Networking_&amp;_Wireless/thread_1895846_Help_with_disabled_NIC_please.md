---
title: "Help with disabled NIC please?"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by graystarr on 2011-12-15
I have Ubuntu 11.10 server and have a Intel 10gb nic installed. I downloaded the driver and did the make install as per the readme file  but when I do a lshw -C network it shows disabled.
Here is what it says

 *-network:1 DISABLED
       description: Ethernet interface
       product: 82598EB 10-Gigabit AF Dual Port Network Connection
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:06:00.1
       logical name: eth5
       version: 01
       serial: 00:1b:21:29:8a:92
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical fibre
       configuration: autonegotiation=off broadcast=yes driver=ixgbe driverversion=3.3.8-k2 duplex=full firmware=1.7-0 latency=0 link=no multicast=yes
       resources: irq:45 memory:df260000-df27ffff memory:df2c0000-df2fffff ioport:ece0(size=32) memory:df23c000-df23ffff


Can someone please help me out on this?

Thanks!!

---

