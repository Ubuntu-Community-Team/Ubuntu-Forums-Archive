---
title: "cannot connect with wep"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by archiepsi on 2008-12-11
I'm running Xubuntu 8.04. I upgraded from 7.1
 I have a dell latitude c610. 20 gig drive 512 meg memory
I have a wireless card with the Ralink rt2500 chipset.
My windows laptop connects fine but when i try to connect Xubuntu do not get an address. 

ifconfig gives the following.
eth0      Link encap:Ethernet  HWaddr 00:08:74:46:49:cd  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe46:49cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15787780 (15.0 MB)  TX bytes:1792595 (1.7 MB)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13900 (13.5 KB)  TX bytes:13900 (13.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:64:82:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22759 (22.2 KB)  TX bytes:15668 (15.3 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:10:60:64:82:d9  
          inet addr:169.254.8.66  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-10-60-64-82-D9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

has any one seen this? :confused:

---

### Post by superprash2003 on 2008-12-11
try setting up static ip in the /etc/network/interfaces file..

---

### Post by al_mckin on 2008-12-11
Have you got the linux-modules-backports package installed?

If you have, it could be this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/297390")

---

