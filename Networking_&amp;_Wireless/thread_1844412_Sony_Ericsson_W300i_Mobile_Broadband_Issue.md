---
title: "Sony Ericsson W300i Mobile Broadband Issue"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by amanisdude on 2011-09-15
Hi all,

I am trying to use my mobile broadband (AT&T) for connecting my computer to the Internet via a USB tether to a Sony Ericsson W300i phone.

The process works great in Windows through the Sony Ericsson PC Suite's Mobile Networking Wizard, but I'm having trouble doing the same in Ubuntu.

I have gone through Ubuntu's built-in Network Connections utility and set up my phone under Mobile Broadband. The phone and computer do connect to the network (as you will see below), but none of my applications can connect through my mobile's broadband.

Here are some network utility outputs to make any assistance easier:

```
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:76:04:a5:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:04:a5:8e  
          inet addr:169.254.7.105  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82470 (82.4 KB)  TX bytes:82470 (82.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.29.95.168  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:58 (58.0 B)  TX bytes:85 (85.0 B)
```

```
lsusb

Bus 005 Device 002: ID 0fce:d053 Sony Ericsson Mobile Communications AB 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
```

```
netstat -nr

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         10.64.64.64     0.0.0.0         UG        0 0          0 ppp0
```

```
Connection Information (from Notification Bar icon)

Active Network Connections
AT&T MEdia Net 1 (default)

Interface:         GSM (ttyACM0)
Hardware Address:
Driver:            cdc_acm
Speed:             Unknown
Security:          Unknown

IP Address:        10.16.3.93
Broadcast Address: 10.16.3.93
Submet Mask:       255.255.255.255
Default Route:     10.64.64.64
Primary DNS:       172.18.7.170
```

As you can see from all the outputs, the phone is recognized and has its own IP address ( 10.29.95.168 ) via PPP. Even Ubuntu says that it's connected in the notification bar. The trick is getting all the applications to use this connection.

I have tried every possible combination restarting, plugging in an ethernet cable to another network, and plugging the phone in (all clearly novice attempts at troubleshooting) to no avail.

If anyone has any suggestions on a solution, that would be awesome. Using my phone's broadband with Ubuntu is part of a greater project. Thanks for any suggests/comments/help!
_______________________________

**Some more info**:
[LIST]
[*]Computer OS: Ubuntu 10.04 LTS on x86 (32-bit)
[*]Phone/Network: Sony Ericsson W300i using AT&T (Cingular)
[*]The world is roughly spherical.
[/LIST]

And, no, pinging its IP from another computer does not return a response, though that could be an AT&T network setting. :D

-**amanisdude**

---

### Post by amanisdude on 2011-09-17
Hey y'all. Any ideas? Are there any resources that could show me how to set up the mobile broadband to see if I'm doing it right? ...Or if the Sony Ericsson W300i is even supported?

---

