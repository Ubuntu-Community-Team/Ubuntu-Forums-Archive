---
title: "Wifi not working on Compaq C700"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by patrickdnj on 2010-11-26
So, I installed ubuntu 10.10 on my Compaq C700, but when I started it up, I am unable to enable wireless. While reading through other boards, it is apparently common for this computer. However, I have not seen anyone address how to enable wifi on ubuntu 10.10
So, do you think someone could show me one to do please?
Sorry, I'm a newb to ubuntu.
Oh, and if this is relevant: 

*-network DISABLED      
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:1a:ec:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:91300000-9130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:f0:06:83
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff

---

### Post by uncaspi on 2010-11-26
Do u get any output from sudo iwlist scan

---

