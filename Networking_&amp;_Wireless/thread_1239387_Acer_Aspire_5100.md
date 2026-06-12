---
title: "Acer Aspire 5100"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by yoshiki2 on 2009-08-13
My vaio had an accident, so I,m back using my aspire 5100, I am booting ubuntu from a disc, but the wireless adapter is not working. How can i make it work?
Explain it like for a 5 years old please XD

---

### Post by superprash2003 on 2009-08-13
it could be tough getting it to work when on the live cd, you should get ubuntu installed.. anyways , do post output of **lshw -C network** from the ubuntu terminal

---

### Post by yoshiki2 on 2009-08-13
If I install it, then what else should I do to make it work?

---

### Post by superprash2003 on 2009-08-14
that depends on the output i had asked for earlier..

---

### Post by yoshiki2 on 2009-08-15
opening new thread with a better title

---

### Post by maticer on 2009-08-16
Hi,

I'm also having problems with wireless on my Acer Aspire 5100. Previously (an hour ago) I had windows on it and didn't had any issues.
In Ubuntu Linux 9.04 I don't see my wireless network and even if I try to connect to it as a "hidden network" it doesn't work. Meanwhile on my other laptop and my phone wlan is still working. Anyway, I already tried to restart my wlan router.

Output of **lshw -C network**:
>   *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:57:88:1e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.111 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:9d:12:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 6e:45:24:5c:f8:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Please for any advice!!!
Thanks!!

---

### Post by maticer on 2009-08-16
OK, Solved! :)
Just had to activate it in System > Administration > Hardware drivers which downloaded drivers so I need to plug it on LAN cable.
After restart all works!

---

### Post by yoshiki2 on 2009-08-16
Can you explain me what to do.. i am new with Ubuntu..

---

