---
title: "New user need Help"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by James@Brunei on 2009-08-04
Dear All,


My Jaunty 9.04 manage to detect my new network card (SiS 900-Based PCI Fast Ethernet Adapter).

I plan to get an internet connection with an _external modem_ and will connect to my new _network card with RJ-45 Ethernet cable_. 

Will it work? How I configure it?

Please help me. 

Here in my place no one knows about how to work with Ubuntu. But I told my friends it is a very stable OS and I am learning.


Thank you

Best regards

Jai James

---

### Post by gjtoth on 2009-08-04
> **James@Brunei said:**
> Dear All,



SiS 900-Based PCI Fast Ethernet Adapter.

The original post left off a lot of details and came across with only the above line.

Are you talking about a CABLE-modem or a regular dial-up modem?  If you're talking about a cable-modem, it should work just fine.  If you're talking about a dial-up modem, why would you need a NIC?

---

### Post by superprash2003 on 2009-08-04
post output of ifconfig from the terminal

---

### Post by James@Brunei on 2009-08-04
Dear friends, 

I am going to use an Alcatel-Lucent cable modem.

The service provider told me the connection could be as following, 

Phone jack - splitter - modem - computer network card.

from splitter to modem using RJ-II Tel cable. 
from modem to network card using RJ-45 Ethernet cable.

Please help me.

Thank you
Jai James
------------------------------------------------------------------
My network card details as follows, 

root@joel-desktop:/home/joel# lshw -C Network

*-network          

description: Ethernet interface
product: SiS900 PCI Fast Ethernet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: 00:16:ec:5b:36:fa
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s


network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: ba:12:f6:89:fa:f0
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
------------------------------------------------------

---

### Post by James@Brunei on 2009-08-05
The modem will be _ADSL modem_ (Alcatel-Lucent brand).

Thank you
Jai James

---

