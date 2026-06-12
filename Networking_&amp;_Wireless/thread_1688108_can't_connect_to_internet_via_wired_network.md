---
title: "can't connect to internet via wired network"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by eric_h22 on 2011-02-15
Hi, my name is Eric, i'm a newbie in Ubuntu.
I'm using Ubuntu as guest (using VMware) and Win XP as host.
In Ubuntu, I can't seem to connect to the internet, I don't know why, 

[IMG]file:///C:/Tmp/moz-screenshot.png[/IMG]  **This is the ifconfig**
  eth0      Link encap:Ethernet  HWaddr 00:0c:29:16:96:bf  
            inet addr:192.168.10.128  Bcast:192.168.10.255  Mask:255.255.255.0
            inet6 addr: fe80::20c:29ff:fe16:96bf/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:403 errors:0 dropped:0 overruns:0 frame:0
            TX packets:3188 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:37407 (37.4 KB)  TX bytes:303420 (303.4 KB)
            Interrupt:19 Base address:0x2000
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
   
  **and this is the iwconfig**
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  pan0      no wireless extensions.
   
  **and this is when I type sudo dhclient eth0**
  Internet Systems Consortium DHCP Client V3.1.1
  Copyright 2004-2008 Internet Systems Consortium.
  All rights reserved.
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
   
  Listening on LPF/eth0/00:0c:29:16:96:bf
  Sending on   LPF/eth0/00:0c:29:16:96:bf
  Sending on   Socket/fallback
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
  DHCPOFFER of 192.168.10.128 from 192.168.10.254
  DHCPREQUEST of 192.168.10.128 on eth0 to 255.255.255.255 port 67
  DHCPACK of 192.168.10.128 from 192.168.10.254
  bound to 192.168.10.128 -- renewal in 861 seconds.


Can anyone help me?
Thx u so much.

---

