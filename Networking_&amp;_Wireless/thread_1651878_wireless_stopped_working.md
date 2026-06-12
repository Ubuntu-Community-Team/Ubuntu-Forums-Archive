---
title: "wireless stopped working"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by KAP123 on 2010-12-23
Hi, I'm using ubuntu 10.10 and it does not connect to my wifi connection anymore. Its detecting my built-in wireless card and I assume that the driver for it is installed as it was working yesterday. However the 'lshw' command shows it as disabled. Here's the output for the 'lshw' command:


  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:03:25:2e:10:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.111 latency=32 multicast=yes
       resources: irq:17 memory:e0206000-e0207fff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1-eth0
       version: 05
       serial: 00:13:ce:b7:14:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:e0208000-e0208fff

And when I right-click the network connections applet it doesn't have the 'Enable Wireless' option. I would appreciate any help.

---

