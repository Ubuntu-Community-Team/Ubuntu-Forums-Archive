---
title: "internet connexion gremlin"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by namluc on 2009-10-27
Hello all

A gremlin has taken over my internet connectivity. I cannot connect to my home network with wireless or wired ethernet, but can connect to my neighbour's, even though  their signal is much much weaker than mine. 

my home network is not the problem.

here is some information that may be of use


luke@luke-laptop:~$ **cat /etc/network/interfaces**
auto lo
iface lo inet loopback


luke@luke-laptop:~$ **sudo lshw -C network**
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:d2:1c:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:24:81:54:3b:a6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:26 memory:febfc000-febfffff ioport:ec00(size=256)

I upgraded to karmic last week, and internet hasn't been the same since. I had a choice of two wireless drivers to use with jaunty but with karmic i have only one, and i think it is not the one i was using a week ago.

regarding the ,png, my network is of course "home", and without any security hurdles to block connexions.

---

