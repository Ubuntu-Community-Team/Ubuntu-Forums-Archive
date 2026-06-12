---
title: "Wireless Draft N"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by colinpat on 2009-03-14
How do you get the iwlagn driver to connect using draft n?
If I boot in XP connection speed is over 100Mb/s with Ubuntu speed never gets higher than 54Mb/s.  I have a Intel Corp PRO/Wireless 4965 AGN 

colin@colin-laptop:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:e2:5a:09
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:3e:04:5d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.100.117 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

---

