---
title: "Wireless problem for Compaq Presario B2800"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by thoemmle on 2011-11-17
hi

I am a beginner in Linux and recently tried to install Ubuntu version 11.10 onto my laptop for a programming project.

For some reason I cannot enable my wireless network and it won't connect to the internet.

This is what I tried to do and the response I got:

terminal => sudo lshw -c network


*-network:0             

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 4

       bus info: pci@0000:02:04.0

       logical name: eth0

       version: 10

       serial: 00:16:35:9f:ae:99

       size: 10Mbit/s

       capacity: 100Mbit/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s

       resources: irq:20 ioport:d800(size=256) memory:feaff000-feaff0ff

  *-network:1

       description: Network controller

       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 5

       bus info: pci@0000:02:05.0

       version: 02

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master

       configuration: driver=b43-pci-bridge latency=64

       resources: irq:18 memory:feafc000-feafdfff

  *-network DISABLED

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:14:a5:79:c4:fb

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


My Laptop model is Compaq Presario B2800.

I tried to connect through land-wire and it worked fine. I guess this is a driver problem for my wireless card?


Any advice will be very much appreciated!

Thanks in advance.

thoemmle

---

### Post by praseodym on 2011-11-17
Hi,

search in the software-center for "b43" and install the firmware packages for the "b43"-driver (**firmware-b43-installer** and **b43-fwcutter**), _not_ those for "b43-legacy"

---

