---
title: "Wireless Authentication Failure"
date: 2013-04-16
forum: Networking &amp; Wireless
---

### Post by charliewarlie on 2013-04-16
Ok, so I have a Zoostorm laptop running Ubuntu 12.10, and whenever I try to connect to my wireless it comes up and asks for my password (which is correct - I've double and triple-checked and other devices are connected no problem) and after a few moments it comes back and asks for it again - it seems to try to connect but then asks for the password again, and never actually gets anywhere.

It's been connected before, but since doing an update and restarting a couple of days ago it just hasn't worked again! It's using the Realtek wireless driver 8723 (which was a huge pain to get working in the first place, but I followed the advice given on some of these forums) but I've been trying to fix this for days now and asked linuxy friends who don't know what else to try - please help!

---

### Post by charliewarlie on 2013-04-16
I just typed this into terminal and here's what I got - I don't know what this means though, or if it's any use or what I should do next.

charlie@charlie-W240EU-W250EUQ-W270EUQ:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 20:68:9d:0c:1b:36
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723e driverversion=3.5.0-28-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:e000(size=256) memory:f7d00000-f7d03fff
 *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 0a
       serial: 00:90:f5:d8:6c:7f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8411-1_0.0.3 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

### Post by sev1 on 2013-04-16
What happens when you try:


sudo /etc/init.d/networking restart

---

### Post by charliewarlie on 2013-04-18
It said command not found...

---

### Post by charliewarlie on 2013-04-21
Anyone have any ideas?

---

### Post by wildmanne39 on 2013-04-21
*Thread moved to **Networking & Wireless**.*

---

