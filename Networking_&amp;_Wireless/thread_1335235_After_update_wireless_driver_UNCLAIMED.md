---
title: "After update wireless driver UNCLAIMED"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by seranus on 2009-11-23
i updated from 9.4 and after the update i cant see my wireless

```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:0a:e4:c3:22:22
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5751m-v3.29a ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:16 memory:b0200000-b020ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:0b:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
       resources: memory:b4000000-b400ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```i got laptop ibm r52 with aethros wifi card and no kill switch as far as i know

---

