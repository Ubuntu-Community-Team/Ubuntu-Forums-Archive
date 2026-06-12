---
title: "Wireless stopped working"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by NoranaC on 2009-01-20
I used to be able to connect to my wireless network every time with no problems.  Other computers could connect to it without any problems also.  
However, about a week ago, I started having problems.  Most of the time, when I start up my computer and it tries to connect to the network but can't.  It asks me for the password.  I enter it in (I've tried both hex and passphrase).  It tries to connect for a while, can't, and then asks me for the password again.  Occasionally, it will start up and connect perfectly just like it did in the good ol' days.  Other computers can connect to the network perfectly fine.
I figured my wireless adapter was dying (Trend Net IEEE 802.11g/2.4 GHz, 108 Mbps) so I got a new one (Rosewill IEEE 802.11b/g/2.4 GHz, 54 Mbps) and it does the exact same thing.  

Please help me!

---

### Post by jsternberg on 2009-01-23
I'm having same problem exactly. Wireless works with Windows computer, but not Ubuntu 8.04. Nothing changed in setup except automatic updates. Any clues appreciated.

2.22.3 (Ubuntu 2008-07-09)
2.6.24-23-generic (#1 SMP Thu Nov 27 18:44:42 UTC 2008)
Dell M1330n, Verizon DSL, Westell 327W

---

### Post by superprash2003 on 2009-01-23
go to the terminal and type lshw -C network and post output here

---

### Post by jsternberg on 2009-01-23
[i'm currently online using my ethernet connection because wireless isn't working]
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:36:2b:c4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:3a:ff:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.46 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

