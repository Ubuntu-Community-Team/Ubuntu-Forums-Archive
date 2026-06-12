---
title: "Wired Cable Connection Gone"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by spadewarrior on 2011-11-30
Hi all,

I came home tonight to find my cable internet access down. I plug straight into the modem via ethernet cable, no routers or wireless or anything complicated. 

After several modem resets to no avail, I thought the cable might be duff, so plugged in via USB. No difference, and my provider tells me the modem appears to be working fine, that there are no problems in the area, and so I should be having no problems... They tried to help further but couldn't as I'm not using Windows... :s

Later, after rebooting the modem some more, the network manager (in xfce) sort-of connects (i.e. ifconfig shows an IPv4 address) but I can't browse the web, receive emails or anything, and I get disconnected again after a couple of minutes.   

Luckily, I also have a (shaky) mobile "broadband" connection, from which I am posting. 

Here's my current ifconfig:

[PHP]
eth0      Link encap:Ethernet  HWaddr 00:19:66:51:8a:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1256 (1.2 KB)  TX bytes:468 (468.0 B)
          Interrupt:22 Base address:0xb400 

eth1      Link encap:Ethernet  HWaddr 00:11:80:ca:58:12  
          inet6 addr: fe80::211:80ff:feca:5812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18712 (18.7 KB)  TX bytes:20165 (20.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:297872 (297.8 KB)  TX bytes:297872 (297.8 KB)

usb0      Link encap:Ethernet  HWaddr 9e:29:37:99:55:aa  
          inet addr:192.168.42.6  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::9c29:37ff:fe99:55aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12112 errors:2 dropped:0 overruns:0 frame:2
          TX packets:9127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15921893 (15.9 MB)  TX bytes:1310074 (1.3 MB)

[/PHP]

and these are for :

eth0 - old ethernet connection (unplugged)
eth1 - modem via usb connection (plugged)
usb0 - current mobile connection (plugged)

For the brief period where the usb connection sort-of worked, ifconfig showed:

[PHP]eth1      Link encap:Ethernet  HWaddr 00:11:80:ca:58:12  
          inet addr:192.168.100.11  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::211:80ff:feca:5812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1180 (1.1 KB)  TX bytes:2340 (2.3 KB)
[/PHP]

Anyone got any suggestions for further troubleshooting / diagnosis? Or is it time to call my provider back?

Any help gratefully received, I'm a total novice with networking!

:)

Cheers.

---

### Post by spadewarrior on 2011-11-30
Never mind, it looks like there's a fault 'in the general area':
[PHP]
Service Disruption

a loss of broadband internet service

Reported on: Wed 30 Nov 2011, 06:44 PM
Estimated fix time: Thu 01 Dec 2011, 09:00 AM
Fault reference: F001817748

[/PHP]

---

### Post by bluexrider on 2011-11-30
Don't you wish everything could fix itself

---

