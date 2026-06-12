---
title: "wirelss problems - please help"
date: 2012-08-26
forum: Networking &amp; Wireless
---

### Post by jimjimicus on 2012-08-26
Hi, 

I am new to linux and ubuntu.

I just installed 12.04.1 on my old Dell XPS 600. Everything worked great except I am unable to connect to my wifi. 

When I go to Network settings it says "Wireless Firmware Missing".  I've tried Additional Drivers, but the only drivers that come up are for my video card.

[COLOR=DimGray]sudo lshw -class network[/COLOR] gave me the following info...[COLOR=DimGray]  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dbff6000-dbff7fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:12:f6:e4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43legacy driverversion=3.2.0-29-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg[/COLOR]

Thanks in advance for you help.

---

