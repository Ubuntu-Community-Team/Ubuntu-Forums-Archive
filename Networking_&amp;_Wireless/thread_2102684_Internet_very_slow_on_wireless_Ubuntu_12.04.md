---
title: "Internet very slow on wireless Ubuntu 12.04"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by dhruvwali on 2013-01-07
Im facing a peculiar problem with Ubuntu 12.04. When I'm on wireless all my webpages load very very slowly but videos + transmission downloads are very fast(actual speed).

I tried all fixes - upgrade kernel,ipv6 disabling,wifi-n diabling etc.. This happened suddenly without me making any changes to network settings. Eralier it was working flawlessly.

Also when I run a windows VM on top of this ubuntu 12.04 there the webpages run very fast(Like normal)..

So stuck on how to fix this issue..

My o/p of lshw :-

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 5c:26:0a:6f:88:c5
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:e6700000-e671ffff memory:e6780000-e6780fff ioport:5040(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a0:88:b4:ca:26:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=17.168.5.3 build 42301 ip=192.168.1.6 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:e6600000-e6601fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by Bucky Ball on 2013-01-07
*Thread moved to **Networking & Wireless***

---

