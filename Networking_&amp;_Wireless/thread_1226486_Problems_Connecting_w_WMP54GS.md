---
title: "Problems Connecting w/ WMP54GS"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Bascal on 2009-07-29
It's weird... I set-up dual-booting vista/linux on my personal computer and followed the instruction from a previous post and got that card hooked up easy as can be. This machine seems to be giving me a bit of trouble though and I don't quite understand why. It's an identical card.

here is the result of sudo lshw -C network > network.txt

  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 78
       serial: 00:01:03:31:d9:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.69.135 latency=32 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:b4:a4:9e:d3:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

It seems to be missing a few things... Any help is appreciated.

---

