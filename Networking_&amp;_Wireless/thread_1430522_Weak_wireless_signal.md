---
title: "Weak wireless signal"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by marlborough on 2010-03-15
I have a weak wireless signal in Ubuntu, but in Vista or XP it;s fine.  Ubuntu I get about 17%, whereas in Vista it's 85-95%.

I'm running 9.10 and the output for lshw is:

  *-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: wmaster0
       version: 20
       serial: 00:14:d1:48:ce:31
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.100 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 ioport:d800(size=256) memory:feaffc00-feafffff
  *-network
       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:1d:92:eb:f7:cc
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:28 memory:fe977000-fe977fff ioport:b880(size=8) memory:fe97e800-fe97e8ff memory:fe97e400-fe97e40f

My router is a Linksys WRT54G2, and my network is WPA2-personal with AES encryption.

Any help is appreciated!

---

