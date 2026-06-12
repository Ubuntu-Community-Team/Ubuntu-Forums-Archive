---
title: "Wireless not working on Acer TravelMate 2304LCi"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by pkaufman on 2010-09-17
Can not get wifi to work?  Tried to turn on switch with no response.  Here is what I get:

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:83:6b:fc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.15.101 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0200000-e0201fff memory:84000000-84003fff(prefetchable)
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3800(size=32) memory:e0203800-e020381f memory:e0203000-e02037ff
ubuntu@ubuntu:~$

---

