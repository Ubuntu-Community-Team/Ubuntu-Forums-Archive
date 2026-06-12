---
title: "WPA not working Ubuntu 8.10"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by stevegr on 2009-01-26
I'm having a hard time getting wpa working on my wireless connection.  The connection works if I have security turned off.  
It's a Toshiba L15 laptop with the infamous Inprocomm internal card, Celeron 1.3 gHz processor, 512 RAM.   

Here's my networking info:

> *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:8a:df:44
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: wlan0
       version: 00
       serial: 00:0e:9b:a8:f4:7d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.53+INPROCOMM,11/04/2004,3.03.1 ip=192.168.10.105 latency=64 link=yes maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:d5:ee:86:bc:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


---

