---
title: "Wireless trouble with Dell Inspiron 1100 and Blitzz wireless card"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by toehead2 on 2009-06-22
I am running Ubuntu 8.04 on a Dell Inspiron 1100 laptop with a Blitzz pcmcia wireless card. Or at least trying to use the wireless card. When I click on the network manager icon at the top of the screen the Blitzz network is displayed however it will not connect. I have tried using the ndiswrapper with Windows drivers from the cd, without luck, not sure if I am doing something wrong? I also read a post listing the supported cards and drivers, which said that my card was supported and worked with madwifi driver. I downloaded and installed linux-restricted-modules madwifi-tools. It appeared to have downloaded and installed ok, but cannot find any trace of it.
Also as stated in another post I typed lshw -C network > network.txt in a terminal with the following output:
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:e7:28:c1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: ADM8211 802.11b Wireless Interface
       vendor: ADMtek
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 11
       serial: 00:e0:98:b0:48:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netwpci driverversion=1.52+PCI Wireless,10/07/2002, 1. latency=80 link=no maxlatency=128 mingnt=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11b

Any and all help welcomed and greatly appreciated. As I have a relative I want to show Ubuntu off to shortly.

---

### Post by toehead2 on 2009-06-22
Anyone?

---

### Post by toehead2 on 2009-06-23
bump

---

### Post by n7gtb on 2010-12-26
Toehead,

Were you able to resolve the issue(s) you mentioned above?  I'm new to Ubuntu (but not linux or Debian) and am considering installing it on an Inspiron 1100 that is equipped with a Linksys network adapter...

I've searched the laptop compatibility thread but no mention of the 1100 (that I could find)...

Thanks,
-Vern.

---

