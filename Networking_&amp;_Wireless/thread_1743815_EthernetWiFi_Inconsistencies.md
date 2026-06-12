---
title: "Ethernet/WiFi Inconsistencies"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by cydetu on 2011-04-29
I did a clean install of 11.04 64bit on a Dell Inspiron 17R. I can access the Internet via both, Ethernet & WiFi (BCM4313), but only if I leave the Ethernet cable connected when the computer starts. Then I can unplug and use wireless normally. If started without connecting the ethernet cable, no WiFi networks show up and even plugging in the cable doesn't work make a connection; restarting with the cable plugged in and everything works again.

When connected and working properly, "sudo lshw -C network" gives the following:

  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 5c:ac:4c:7e:51:21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:49:d8:31
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.11.53 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)

Any help?

---

