---
title: "Cannot connect to internet: Eee 1001P with 10.04"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by limitless_scenarios on 2010-08-08
Hello! I recently installed Ubuntu Netbook Edition 10.04 on a  brand new Asus Eee PC 1001P. When I plug in my ethernet cable the network icon at the top of the screen indicates "Auto eth0 Connection Established" however the internet does not work. Does anyone know how to fix this problem? I'm completely new to Ubuntu. Please help.

---

### Post by dineshs on 2010-08-08
Please post the output of the following commands
```
ifconfig -a
```and
```
ping 4.2.2.1 -c3
```

---

### Post by limitless_scenarios on 2010-08-08
Here is the output:

eth0      Link encap:Ethernet  HWaddr 48:5b:39:23:dd:d6  
          inet addr:@@.@30.233.8  Bcast:@@.@30.233.255  Mask:255.255.254.0
          inet6 addr: fe80::4a5b:39ff:fe23:ddd6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:367 (367.0 B)  TX bytes:3841 (3.8 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14032 (14.0 KB)  TX bytes:14032 (14.0 KB)

PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
From 99.230.233.8 icmp_seq=1 Destination Host Unreachable
From 99.230.233.8 icmp_seq=2 Destination Host Unreachable
From 99.230.233.8 icmp_seq=3 Destination Host Unreachable

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2016ms
, pipe 3

---

### Post by limitless_scenarios on 2010-08-09
Here's some more info:

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:002c] (rev 01)

---

