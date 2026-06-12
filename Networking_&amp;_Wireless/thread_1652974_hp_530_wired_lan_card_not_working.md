---
title: "hp 530 wired lan card not working"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by abhijeetdesai on 2010-12-26
hi all,
the wired lan card on hp 530 is not working the wireless works fine plz help me.
thanks
abhijeet

```
sudo lshw -C network
```returns 

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:2a:65:5a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-24-generic firmware=15.32.2.9 ip=192.168.0.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:f0000000-f0000fff
  *-network [COLOR=Red]_**UNCLAIMED**_[/COLOR]
       description: Ethernet controller
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
       resources: memory:f0101000-f0101fff ioport:2000(size=64)

---

### Post by mips on 2010-12-26
What is not working?

Have you tried switching between the wireless & wired via the network manager.

Tried changing from DHCP to Static IP or playing with the speed/duplex settings.

Also paste the output of **sudo ifconfig -a** here.

---

### Post by abhijeetdesai on 2010-12-26
thats not the problem the card is not detected in ifconfig -a 
it shows only the wifi lancard

---

