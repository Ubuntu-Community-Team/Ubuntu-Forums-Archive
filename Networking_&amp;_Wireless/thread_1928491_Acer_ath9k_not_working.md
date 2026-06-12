---
title: "Acer ath9k not working"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by RoushAH on 2012-02-20
Hey, y'all, apparently my attempt to edit a word document in openoffice.org caused my network adapter to be disabled, and now I can't reenable it.  I'm on an Acer Aspire 5732z, and when I run lshw -C network, I get the following:


 *-network DISABLED      
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 0c:ee:e6:dd:6c:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:94600000-9460ffff


How do I reenable the network?  HELP!!

---

### Post by chili555 on 2012-02-20
You might read this thread and see if it helps. [http://ubuntuforums.org/showthread.php?p=11296301](http://ubuntuforums.org/showthread.php?p=11296301)

---

