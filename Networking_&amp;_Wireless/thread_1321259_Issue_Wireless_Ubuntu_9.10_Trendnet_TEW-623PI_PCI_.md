---
title: "Issue: Wireless Ubuntu 9.10 Trendnet TEW-623PI PCI card"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by kpkelly20 on 2009-11-09
Hi guys, I have a new install of Ubuntu and my wireless card (TrendNet TEW-623PI) is not recognized right away.  I am new to the OS... I tried using Ndiswrapper a couple times with the windows driver on the PCI card CD but it led my console to lock up twice...

Any help would be appreciated.  Thanks!!

Kyle

I will answer the template questions here:
1) machine brand:  built my PC, AMD athlon II x2 250 running 64 bit Ubuntu , Gigabyte motherboard

2) lspci:
03:07.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190

3) iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

4) lsmod - I don't see anything here about my wireless card... I could be wrong though

5) dmesg - again, can't see anything related to network

6) Network config

*-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:ce00(size=256) memory:fdcff000-fdcfffff


7) scan for networks -  iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

8) Ubuntu version : 9.10

9) kernel/architecture:  2.6.31-14-generic x86_64

10)  Restarting the network
* Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

---

