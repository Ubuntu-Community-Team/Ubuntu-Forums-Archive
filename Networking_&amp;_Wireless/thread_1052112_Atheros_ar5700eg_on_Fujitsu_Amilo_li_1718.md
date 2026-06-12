---
title: "Atheros ar5700eg on Fujitsu Amilo li 1718"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by dark0dave on 2009-01-27
This is for a Fujitsu Amilo li 1718 with an ar5700eg for ubuntu 8.10 I have tried many a method and I can't seem to find a solution.

_sudo lshw -C network yeilds_
 [B]*-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:c0:a8:f6:0b:5e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:8f:09:a6
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.9 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:f6:90:45:e5:a3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/B]

---

### Post by dark0dave on 2009-01-27
Also I can not see any networks obviously, any help would be great!
thanks

---

### Post by dark0dave on 2009-01-27
Another issue is that the wireless light for the computer mentioned above does not turn on!

---

### Post by dark0dave on 2009-01-27
Stop the presses I found the solution in one of my early posts, all credit goes to Oli1122 for finding the link [http://www.amilo-forum.com/topic,102...rs-needed.html](http://www.amilo-forum.com/topic,102...rs-needed.html) +++++++++++++++++++++++++++++rep

---

### Post by dark0dave on 2009-06-02
[http://ubuntuforums.org/showthread.php?t=986288&highlight=amilo+li+1718](http://ubuntuforums.org/showthread.php?t=986288&highlight=amilo+li+1718)
this works for me. Thanks guys.

---

