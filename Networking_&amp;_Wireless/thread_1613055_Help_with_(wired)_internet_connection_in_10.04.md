---
title: "Help with (wired) internet connection in 10.04?"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by newb_untu on 2010-11-04
I've just installed the 64 bit 10.04 onto my new netbook, with ample specs to run the full desktop version rather than the stripped down netbook version.  My only problem (at the moment) is that my wired internet connection is not recognized within the operating system, yet while I was downloading/installing Ubuntu it had no problem finding and using the connection then.  When I boot into Windows 7 or plug the ethernet cable into my Mac, the connection is established immediately, and no need for manual entering of anything because everything is auto-detected.  Can someone steer me in the right direction on this?  

The really strange thing is I've run Ubuntu off a USB stick and when booting off that the wired connection was immediately recognized after startup.

---

### Post by newb_untu on 2010-11-04
If it matters at all, eth0 doesn't show up anywhere when I type ifconfig into terminal

---

### Post by newb_untu on 2010-11-04
Wow... 

Anyone?!

Please??

96 views and no one wants to chime in? :(

---

### Post by dineshs on 2010-11-05
what do you get for```
sudo lshw -C network
```?

---

### Post by newb_untu on 2010-11-05
Here is what I got from that command:


*-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:4f:02:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f9ff0000-f9ffffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f5fc0000-f5ffffff ioport:dc00(size=128)

---

### Post by dineshs on 2010-11-05
> *-network UNCLAIMED
description: Ethernet controller
product: AR8152 v2.0 Fast EthernetTry if this helps
[http://ubuntuforums.org/showthread.php?p=10013704#post10013704](http://ubuntuforums.org/showthread.php?p=10013704#post10013704)
or
[http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

---

