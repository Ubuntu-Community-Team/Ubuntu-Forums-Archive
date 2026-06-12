---
title: "Cant enable wireless internet"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by zebraneo on 2009-12-15
I have a new Lg laptop and I can't get enable wireless INTERNET
.

---

### Post by t0mppa on 2009-12-15
Ok, you're going to have to give a little more information than that. Do you mean not being able to tick the "Enable _W_ireless" on the Network Manager or that you're having a problem with getting networks show up or to connect to them? If either of the latter ones, then open up a terminal, run **lshw -c network** and post back with the results.

---

### Post by zebraneo on 2009-12-16
I noticed that network is unclaimed what do I do


juilie@juilie-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:36:e6:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.0.0.4 latency=0 multicast=yes
       resources: irq:27 ioport:3000(size=256) memory:90010000-90010fff(prefetchable) memory:90000000-9000ffff(prefetchable) memory:90020000-9002ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:94000000-9400ffff
juilie@juilie-laptop:~$

---

### Post by bkratz on 2009-12-16
Did a quick search (above) and found this link, hope it is helpful

[http://ubuntuforums.org/showthread.php?t=1313132&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1313132&highlight=RT3090)

---

### Post by zebraneo on 2009-12-16
Thank you I the link is a patch, How do I use the patch??? \Thanks

---

### Post by bkratz on 2009-12-16
> **zebraneo said:**
> Thank you I the link is a patch, How do I use the patch??? \Thanks




Look at post #18, he gives a link to a "how to"

---

