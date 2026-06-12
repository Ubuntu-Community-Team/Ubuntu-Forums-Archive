---
title: "Atheros  AR9285 wireless config"
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by airper on 2011-08-13
Hi folks, 
I'm having some real difficulties getting an Internet connection of any sorts on a Toshiba Satellite R830-145
using 11.04
The wireless card is an Atheros AR9285, and is using the ath9k driver. I've been trying to follow the thread below by wildmanne39 and looked to be making a little progress

[http://ubuntuforums.org/showthread.php?t=1811424&highlight=AR9285+wpa2](http://ubuntuforums.org/showthread.php?t=1811424&highlight=AR9285+wpa2)

Network Manager was listing all the available wireless network and was trying to connect. Powered up this morning and all my networks options are now removed from Network Manager

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

``````

sudo lshw -C network
[sudo] password for wayne: 
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: e8:9d:87:eb:5f:28
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:40 memory:c4800000-c481ffff memory:c482a000-c482afff ioport:3060(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c2600000-c260ffff

```I've searched here and on google, I know the AR9285 is not the easiest of cards and looked at the possibility of using mad-wifi or compat drivers, but they don't seem to have solved the problems either. The thread above looked the most promising, but now I've gone a big step backwards and I just can't see why.

---

