---
title: "Ubuntu/Belkin ppc usb adapter n750"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by Redzky on 2013-02-25
I am currently trying to make a Belkin n750 USB wifi adapter work on a ppc g4 aluminum laptop with ubuntu 12.04 lts installed. I did everything in this tut: [http://ubuntuforums.org/showthread.php?t=1986992&page=2](http://ubuntuforums.org/showthread.php?t=1986992&page=2) but still not working.

I also downloaded the drivers from [http://www.wikidevi.com/wiki/Belkin_F9L1103](http://www.wikidevi.com/wiki/Belkin_F9L1103) but the guide included with the drivers was a bit over my head and not very specific.

If someone could please give me the time to get this working, it would be greatly appreciated. Thanx.

---

### Post by cariboo on 2013-02-27
Could you open a terminal, and type the following command:

```
sudo lshw -C network
```

and paste the output in your next post.

---

### Post by Redzky on 2013-02-27
> **cariboo907 said:**
> Could you open a terminal, and type the following command:

```
sudo lshw -C network
```and paste the output in your next post.


This is the output:

```

*-network                       description: Network controller        
product: BCM4306 802.11b/g Wireless LAN Controller        
vendor: Broadcom Corporation        
physical id: 12        
bus info: pci@0001:10:12.0 
       version: 03        
width: 32 bits        
clock: 33MHz        
capabilities: pm bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=16        
resources: irq:52 memory:a0006000-a0007fff 
  *-network        description: Ethernet interface        
product: UniNorth 2 GMAC (Sun GEM)        
vendor: Apple Inc.        physical id: f        
bus info: pci@0002:24:0f.0        
logical name: eth0        
version: 80        serial: 00:11:24:7b:a9:64        size: 10Mbit/s 
       capacity: 1Gbit/s        
width: 32 bits        clock: 66MHz        
capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        
configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=1.0 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10Mbit/s 
       resources: irq:41 memory:f5200000-f53fffff memory:f5100000-f51fffff 
  *-network:0        
description: Wireless interface        
physical id: 1        
bus info: usb@1:2        
logical name: wlan1        serial: ec:1a:59:28:46:e1 
       capabilities: ethernet physical wireless        
configuration: broadcast=yes driver=r8712u ip=192.168.1.13 multicast=yes wireless=IEEE 802.11bgn 
  *-network:1 DISABLED 
       description: Wireless interface        
physical id: 2        
logical name: wlan0        serial: 00:11:24:8e:28:26        
capabilities: ethernet physical wireless 
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-38-powerpc-smp firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
```So that's the output. Here is a clearer look in pastebin: [http://paste.ubuntu.com/5569865/](http://paste.ubuntu.com/5569865/)

---

### Post by Redzky on 2013-03-03
Ok, I guess I'll just take it back.

---

