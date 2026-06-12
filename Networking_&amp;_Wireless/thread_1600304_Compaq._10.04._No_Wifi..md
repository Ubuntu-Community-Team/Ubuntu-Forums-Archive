---
title: "Compaq. 10.04. No Wifi."
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by genesisleighton883BC on 2010-10-18
p { margin-bottom: 0.08in; }  Alrighty folks... here's the skinny: I installed Ubuntu version 9.10, updated to 10.04 via update manager. No wifi. I did about everything under the sun I could think of to get it back online - even went off UbuntuForums for a solution. I came up with a big 0 for my trouble.

So I did a clean install of 10.04 and here I am - no wifi but, see I have learned, I'm asking for help here. What can I try so I can have my beloved wifi back on my computer??

---

### Post by johnnytm on 2010-10-18
Need to know what wireless card you have first.

---

### Post by genesisleighton883BC on 2010-10-18
Duh. Sorry about that. 



eridian@eridian:~$ **sudo lshw -C network**
[sudo] password for eridian: 
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: c4:17:fe:95:33:3b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:90100000-9010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: c8:0a:a9:2e:1f:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:2000(size=256) memory:90010000-90010fff memory:90000000-9000ffff memory:90020000-9002ffff

---

### Post by genesisleighton883BC on 2010-10-19
Twenty one hours later... 

Okay, even tried downloading HP's driver for it and running it through WINE, no dice. Any thoughts from any of you???

---

