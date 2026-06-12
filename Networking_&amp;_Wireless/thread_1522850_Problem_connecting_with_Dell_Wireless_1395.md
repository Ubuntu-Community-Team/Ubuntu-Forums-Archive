---
title: "Problem connecting with Dell Wireless 1395"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by pavlovgg on 2010-07-02
Currently I have the latest version of Ubuntu 10.04. My laptop is Dell Inspiron 1525 and my wireless card (as saying in Windows is) Dell Wireless 1395 WLAN.

Recently I've decided to leave Windows and switch to Linux, more specifically Ubuntu. I'm quite new to linux systems and this fact is not making fixing the above problem easy.

Another important thing is that **I DON'T have internet through the LAN card** since it's broken and I'm currently left with just the wireless, which as stated above is not working. In this situation** I can't update the Ubuntu system** through internet and get the necessary driver for the wireless.

I've tried** [this (link) ]("http://www.youtube.com/watch?v=v0Ist9aEKEg&feature=related")**tutorial, which probably gets as close as possible to my situation, since it installs ***ndiswrapper*** from the source and the*** wireless card driver*** from the source as well. But just in the final stage of this tutorial, when it seemed to have the "ndiswrapper" installed and the wireless driver as well, something when wrong and the following error occured: 
 *When I type "**ifconfig wlan0 up**" it says&#65279; "**SIOCSIFFLAGS: No such file or  directory**"                 *

So now I'm in the situation where I can't install my wireless card's driver and the wireless card is my only way of connecting to the internet. Here I am asking for advise, help or suggestions.

This is my network stats from the Ubuntu console:

&#65279;```
  *-network                 
       description: Ethernet interface  
       product: 88E8040 PCI-E Fast Ethernet Controller  
       vendor: Marvell Technology Group Ltd.  
       physical id: 0  
       bus info: pci@0000:09:00.0  
       logical name: eth0  
       version: 12  
       serial: 00:1d:09:59:67:d3  
       size: 100MB/s  
       capacity: 100MB/s  
       width: 64 bits  
       clock: 33MHz  
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s  
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)  
  *-network  
       description: Network controller  
       product: BCM4312 802.11b/g  
       vendor: Broadcom Corporation  
       physical id: 0  
       bus info: pci@0000:0b:00.0  
       version: 01  
       width: 64 bits  
       clock: 33MHz  
       capabilities: pm msi pciexpress bus_master cap_list  
       configuration: driver=b43-pci-bridge latency=0  
       resources: irq:17 memory:fe7fc000-fe7fffff  
  *-network DISABLED  
       description: Wireless interface  
       physical id: 2  
       logical name: wlan0  
       serial: 00:16:44:bf:c9:3c  
       capabilities: ethernet physical wireless  
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

---

### Post by pavlovgg on 2010-07-02
Problem solved. What happened is that I got tired of trying and thinking of how many things I tried maybe everything got mixed, therefore I installed a fresh copy of Ubuntu 10.04. With the difference that this time the LAN cable was plugged-in during the installation and when Ubuntu started it automatically found drivers and was online. Hopefully I can fix the wireless now with this connection and the updates available.

However, if somebody has a solution to the situation described above it would be wonderful for others in my situation, having to install these drivers without any internet connection. Since all the tutorials I found are not considering this option (not being connected at all).

---

