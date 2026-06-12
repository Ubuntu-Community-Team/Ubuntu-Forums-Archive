---
title: "[64 bits] BCM43225 finds networks but doesn't connect"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by franiodoro on 2011-07-25
Hello,

I'm having a strange issue with this network adapter in Ubuntu 11.04 2.6.38-10-generic. The thing is that it finds the networks around but it's not possible to connect to any network. The network has no wep or wpa password protection, the only protection is MAC filtering protection. If I use a Belkin USB network adapter the computer connects without any problems but if I use the BCM43225 the icons seems to be trying to connect but at the end the connection fails. Here is the info about my network adapters:


 *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:XX:XX:XX
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:b3400000-b340ffff
  *-network
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 88:9f:fa:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2400000-b2403fff
  *-network
       description: Wireless interface
       physical id: 3
       bus info: usb@2:1.1
       logical name: wlan1
       serial: 00:21:bd:dd:1b:be
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-10-generic firmware=1.7 ip=192.168.1.35 link=yes multicast=yes wireless=IEEE 802.11bg
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty
Linux maria-TravelMate-5742 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Thank you

---

### Post by wildmanne39 on 2011-07-25
Hi, it look like you have a usb adapter and you want to get your internal adapter working is that correct?

While you have the usb adapter plugged in it will conflict with your internal card.

Please run these commands in a terminal
```
lsmod
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

