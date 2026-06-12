---
title: "I need help with my wifi on my toshiba laptop satillite-s875d"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by chrissy.millichamp on 2012-11-07
I cant connect to my network cause my wifi wont work. Heres is what I got by typing this 
sudo lshw -C network in the terminal,*-network UNCLAIMED     [C
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 4c:72:b9:51:49:e9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:2000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
                                                                                     Theres btw nothing in the additional drivers updates for the card. And I tried other forums didn’t get any results... plz HELP!
Thnxs in advance

---

### Post by alkh3myst on 2012-11-08
Hi, chrissy.millichamp. Toshiba users have been reporting that they needed a wireless driver upgrade. The package for that is "linux-backports-modules-cw-". Also your wired connection is usually at eth0, and the wireless at eth1. Unfortunately, I'm not sure if that's part of the problem or not, or how to change the logical name for that connection. Also, it's not fair, but this works. Stuff posted in the Beginners section usually gets the fastest responses. Maybe it's the pity response.

:popcorn:

---

### Post by alkh3myst on 2012-11-08
I forgot something. You didn't use any keywords when you posted this question. That makes it harder for people to find it. Something like: wireless, toshiba, ubuntu 12.10.

---

### Post by chrissy.millichamp on 2012-11-08
I installed the package, and it wont work, plus my direct Ethernet wont work no more... strange

---

