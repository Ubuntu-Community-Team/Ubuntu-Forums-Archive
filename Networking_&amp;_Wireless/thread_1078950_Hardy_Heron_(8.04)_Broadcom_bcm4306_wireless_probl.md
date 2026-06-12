---
title: "Hardy Heron (8.04) Broadcom bcm4306 wireless problems."
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Dark_vampel on 2009-02-23
Mucho help needed. I cannot for the death 
of me find a way to get my wireless to work. I've looked all over and found method and method and none seem to work...
I can't get ndiswrapper to work quite right I don't know if it is the drivers that I've try or not.
I've also dappled a little with fw-cutter to no avail.
Any ideas?

This is my info.

```
dark@Marc:~$ sudo lshw -C network
[sudo] password for dark: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0f:20:ca:b1:8a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.68 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:5c:9b:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by Dark_vampel on 2009-02-23
*bump*

---

### Post by Dark_vampel on 2009-02-23
*bump* ... :frown:

---

### Post by Dark_vampel on 2009-02-24
*Bumpity*

---

