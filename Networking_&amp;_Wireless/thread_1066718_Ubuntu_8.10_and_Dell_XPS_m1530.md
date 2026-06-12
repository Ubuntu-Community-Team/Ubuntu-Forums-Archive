---
title: "Ubuntu 8.10 and Dell XPS m1530"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by dagjs on 2009-02-11
Dear all! 

I have used Ubuntu for some time, but I have problems with the wireless network configuration on my new laptop. I mostly work on Ubuntu, but I have a dual installation with Vista and Ubuntu for some job issues.

I have a XPS m1530 with A12 bios version. The problem is that Vista manage to log into internet using wireless, Ubuntu not. Typing 

> sudo lshw -class network

provide the following information:

>   *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:03:f1:c6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:21:5c:91:03:53
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:ea:cc:53:57:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Any ideas how to solve this?

In advance, thanks for all help!

---

### Post by ieee488 on 2009-02-11
It looks like your wireless card has Intel chipset.
Do a search on these forums on that particular chipset and see what comes up.

---

