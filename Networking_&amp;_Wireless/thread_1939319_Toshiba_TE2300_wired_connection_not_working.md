---
title: "Toshiba TE2300 wired connection not working?"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by tonnn on 2012-03-11
Hello!
I am newbie in Ubuntu. I use Lubuntu version 11.10. I have a wireless connection and that is working fine but wired connection not.
lshw -C network```
*-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 04
       serial: 00:04:23:80:82:cb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.99 latency=128 link=yes maxlatency=34 mingnt=2 multicast=yes wireless=IEEE 802.11b
       resources: irq:6 memory:e0001000-e0001fff
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82801DB PRO/100 VE (CNR) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:a0:d1:d7:79:14
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=128 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:e0000000-e0000fff ioport:c000(size=64)
```I have a Ethernet chipset Intel 82562 instead of 82801DB. In [there]("http://ubuntuforums.org/showthread.php?t=872739") is somekind of solution what i tried but no luck.
Any suggestions?

---

### Post by marinara on 2012-03-13
some computers require you to disable the wireless before you plug up

---

### Post by Bucky Ball on 2012-03-13
> **marinara said:**
> some computers require you to disable the wireless before you plug up

Which ones exactly? Never heard of that one.

I have a Toshiba and can plug in no problem (without disabling wireless).

---

### Post by tonnn on 2012-03-14
No that is not change nothing.

---

### Post by tonnn on 2012-03-17
Well i discoverd that, when I suspend the machine and power it up the wired connection is working, but after restart, hibernate, shutdown it wont. It happends yesterday after update manager system update. The network driver is the same 82801DB PRO/100 VE (CNR) Ethernet Controller.

---

