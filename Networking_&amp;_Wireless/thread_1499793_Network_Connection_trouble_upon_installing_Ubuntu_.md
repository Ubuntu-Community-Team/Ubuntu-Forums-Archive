---
title: "Network Connection trouble upon installing Ubuntu 10.04 with Intel (R) Pro 100 /ve"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by crazyoldmorrice on 2010-06-02
Hi, 
 
I've just installed ubuntu 10.04 via wubi through windows 7. Installation seems to have worked fine but i'm having trouble establishing a network connection. 
 
The network card is an Intel (R) Pro 100 /ve.
 
It seems that the card has tried to establish a connection via IPv6, when I believe it should be connecting via IPv4.
 
Any help would be very appreciated.
 
Alex

---

### Post by crazyoldmorrice on 2010-06-02
> **crazyoldmorrice said:**
> Hi, 
 
I've just installed ubuntu 10.04 via wubi through windows 7. Installation seems to have worked fine but i'm having trouble establishing a network connection. 
 
The network card is an Intel (R) Pro 100 /ve.
 
It seems that the card has tried to establish a connection via IPv6, when I believe it should be connecting via IPv4.
 
Any help would be very appreciated.
 
Alex
 
I've also got some more information to add...
 
 
**00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02) **

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01) 
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01) 
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01) 
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) 
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) 
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01) 
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01) 
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01) 






*-network 
description: Ethernet interface 
product: PRO/100 VE Network Connection 
vendor: Intel Corporation 
physical id: 8 
bus info: pci@0000:04:08.0 
logical name: eth0 
version: 01 
serial: 00:19:d1:ef:dd:f6 
size: 100MB/s 
capacity: 100MB/s 
width: 32 bits 
clock: 33MHz 
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s 
resources: irq:20 memory:90000000-90000fff ioport:1000(size=64) 






eth0 Link encap:Ethernet HWaddr 00:19:d1:ef:dd:f6 
inet6 addr: fe80::219:d1ff:feef:ddf6/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:1047 errors:0 dropped:0 overruns:0 frame:0 
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:128415 (128.4 KB) TX bytes:1152 (1.1 KB) 



lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:44 errors:0 dropped:0 overruns:0 frame:0 
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:2960 (2.9 KB) TX bytes:2960 (2.9 KB)

---

### Post by kirkface8 on 2010-10-12
hey did you end up getting this working
i am having the exact same problem

---

