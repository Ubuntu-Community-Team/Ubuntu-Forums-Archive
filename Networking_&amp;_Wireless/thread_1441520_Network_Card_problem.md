---
title: "Network Card problem"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by robinabo on 2010-03-28
Well I seem to have a problem with my laptops wireless card. My card has both bluetooth and the standard 802.11a/b/g capability. Ubuntu 9.10 which is the version I have recognizes the bluetooth part of the card because the driver is supported. However for the wireless part of the card, I have to manually activate the driver. And somehow when the computer reboots, the driver remains activated but it isn't in use, requiring me to deactivate it and then reactivate it manually in order to use my wireless. I'm sort of a newbie since I've tried ubuntu before, but this is the first time I'm using it as a main OS, since vista is just too damn f***ed up. The driver's name is "Broadcom STA wireless driver", with the description being: These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, **BCM4312(my card)**-, BCM4321-, andBCM4322-based hardware. Using the lshw command I got this information on my card: >  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 01
       serial: 00:1a:73:38:59:b4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.91.9 ip=192.168.1.40 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:b3000000-b3003fff
This is the primary problem I'm suffering from. I can still access the internet, but that requires me to go through the time of deactivating and reactivating the driver. Is there any way to fix this?
Side problems include the screen remaining off, and non of the keys wake the computer from sleep mode, and a sort of static discharge from my speakers which precedes any sound made.
If anybody could help me I would be much obliged.

---

### Post by robinabo on 2010-03-30
/Bump

---

### Post by robinabo on 2010-04-02
So was just wondering what are the chances of fixing this problem?

---

### Post by Iowan on 2010-04-04
I presume you used Network Manager to set up the wireless interface? Is it set to "Connect Automatically"?

---

### Post by robinabo on 2010-04-05
Yes I set it to Connect Automatically. This is why my card automatically connects after the driver finishes installing.

---

