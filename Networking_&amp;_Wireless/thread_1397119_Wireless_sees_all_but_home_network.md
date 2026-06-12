---
title: "Wireless sees all but home network"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by cnja on 2010-02-02
Ok guys got a good one for ya.. long story made short.
Gateway NV52 series laptop with Atheros AR5B93 wireless.
When I first installed Ubuntu 9.10 64bit wireless worked for a while then dropped.
did some searching and discovered it was a common problem, read through the pile of troubleshooting tips, and did everything that everyone suggested.
Installed NDISWRAPPER, uninstall gnome-network-manager and installed WICD.
wireless detects every wireless network in the neighborhood except mine.  I know my network is working because I am able to connect with another laptop wireless.
Even installed the wifi radar app, still doesn't see my network, but sees everyone elses.
Router is set upto broadcast in B and G mode. lshw -C network and got the following

 *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 0c:60:76:1c:f6:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathwx driverversion=1.55+,06/03/2009,7.7.0.329 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:f0400000-f040ffff

any help would be greatly appreciated....really pulling my hair out on this one.

---

### Post by cnja on 2010-02-15
fixed my problem, dumped, ubuntu 9.10, reinstalled, and then installed the backports, fixed the wireless problem.

---

