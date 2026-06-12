---
title: "Posible source of disabled wireless?"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2010-06-28
[I]Hello All

My wireless was working fine for about a year using 9.10 until I installed an update about May 28 2010.  After that my HP laptop did not recognize any wireless routers including my Netgear. In early June I upgraded to 10.04 hoping it would help,but no help.  My HP laptop has:  
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.

**Dose the following apply when looking for the source of my disabled wireless** found at: [/I] [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

Setting wireless regulatory domain via module option no longer supported.

Ubuntu 10.04 LTS enables the CRDA wireless regulatory framework for controlling which wireless channels are usable and visible in a particular location. If you previously had to use the module option similar to that below in /etc/modprobe.d/options.conf to allow access to certain channels in your locality then you may find that wireless will not function at all: 
options cfg80211 ieee80211_regdom=EU 
You should remove this kernel module option on upgrade from releases earlier than Ubuntu 9.04 and use the iw*reg command instead. 
(This change was made in Ubuntu 9.04.)


*Here are the results for the Code sudo lshw -C network*

  *-network               

       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth0

       version: 02

       serial: 00:1f:16:76:dc:4b

       size: 100MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100MB/s

       resources: irq:26 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)

  *-network DISABLED

       description: Wireless interface

       product: AR5001 Wireless Network Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wlan0

       version: 01

       serial: 00:24:2b:af:c5:33

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg

       resources: irq:17 memory:d2600000-d260ffff

[I]Thank you 
Gordon33[/I]

---

### Post by gordon33 on 2010-06-29
SEE:

[http://ubuntuforums.org/showthread.php?t=1520352](http://ubuntuforums.org/showthread.php?t=1520352)

---

