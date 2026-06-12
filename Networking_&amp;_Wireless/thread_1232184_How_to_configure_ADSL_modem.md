---
title: "How to configure ADSL modem"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by James@Brunei on 2009-08-05
Dear friends, 

I am going to use an Alcatel-Lucent ADSL modem in _Jaunty 9.04_.

My service provider told me the _connection_ could be as per _following_, 

    _Phone jack *to* splitter *to* modem *to* computer network card._

The cable connection as per following, 
    from _splitter to modem_ using _RJ-II Tel cable_. 
    from _modem to network card_ using _RJ-45 Ethernet cable_.
 


Will it work ? How I configure it? Can I use Network Manager or Network tool for connection?

Here in my place no one knows about how to work with Ubuntu. 



 
 Please help me.

Thank you

Best regards, 
Jai James
 ------------------------------------------------------
_My network card details as follows,_ 

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

