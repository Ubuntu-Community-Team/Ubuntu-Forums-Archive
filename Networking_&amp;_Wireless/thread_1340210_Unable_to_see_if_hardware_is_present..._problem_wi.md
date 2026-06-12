---
title: "Unable to see if hardware is present... problem with WiFi"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by kulobrad on 2009-11-28
Hello, i have a ''little'' problem. I have installed ndiswrappers thru Synaptic, when i add my driver, it says ''Unable to see if hardware is present'' and then it says ''Hardware present:Yes'' but doesn't work, i know that i have to write something into temrinal. i followed one thread but it didn't help me.

when i wrote to terminal :''sudo lshw -C network'' appeared:

*-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:58:36:39
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v2.19 ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:f5100000-f510ffff
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:1e:65:e9:92:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:f5200000-f5201fff



Please. What should i do? I'm new to linux. Thanks

---

