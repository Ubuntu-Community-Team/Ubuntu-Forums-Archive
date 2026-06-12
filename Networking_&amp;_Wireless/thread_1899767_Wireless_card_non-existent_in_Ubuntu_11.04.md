---
title: "Wireless card non-existent in Ubuntu 11.04"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by sword_guy on 2011-12-24
Hello all,

I've gone through a lot of other posts and walkthroughs, but I can't figure out how to fix this problem.  Here's what happened:

Upgraded to 11.04
Noticed that Grub was still showing 10.04 with some old kernels (card worked fine when selecting those older versions)
Updated Grub (after installing version 1.99)
Rebooted with newest working kernel (the pae kernel wouldn't work)
Wireless internet disappeared.  The card is not even recognized.  Here's the output of lshw -class network:

*-network               
       description: Ethernet interface
       product: NetLink BCM57788 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 01
       serial: 00:22:4d:4b:d9:f8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb ip=10.0.0.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:49 memory:e3200000-e320ffff

I've tried a few things, but nothing makes the card appear.  It's a Trendnet TEW-443PI.

Any ideas?

---

