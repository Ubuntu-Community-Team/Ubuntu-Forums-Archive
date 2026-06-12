---
title: "Internet Sharing on Ubuntu Desktop 10.04"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by denyboy on 2010-05-08
On PC1 i have internet ADSL connection

PC 1 (UBUNTU)
Static IP 192.168.137.1
Mask 255.255.255.0
Gateway 0.0.0.0

wireless network between them

PC2 (Windows XP)
Static IP 192.168.137.2
Mask 255.255.255.0
Def.Gateway 192.168.137.1

I created network with settings above. I can create connection. I can even connect PC2 to PC1. And i can even ping PC1 from PC2 and vice versa.

I even added 
net.ipv4.ip_forward = 1
to /etc/sysctl.conf

but internet is not working on PC2 (windows xp).

---

### Post by denyboy on 2010-05-09
PLEASE ANY HELP:


[SIZE="2"]iwconfig[/SIZE]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"LOLAC"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 46:45:36:DF:A1:B1   
          Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
pan0      no wireless extensions.

ppp0      no wireless extensions.


[SIZE="2"]ifconfig[/SIZE]
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:01:28:1b  
          inet6 addr: fe80::21f:c6ff:fe01:281b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13390381 (13.3 MB)  TX bytes:2273789 (2.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.146.152.247  P-t-P:89.146.128.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:12681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:13102999 (13.1 MB)  TX bytes:1979352 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:51:dc:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:1c:f0:9a:26:fc  
          inet addr:192.168.137.1  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:fe9a:26fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:92094 (92.0 KB)  TX bytes:8573 (8.5 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:15:af:51:dc:d3  
          inet addr:169.254.10.246  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

---

### Post by Iowan on 2010-05-09
The **wlan0:avahi** doesn't look like a good thing.
I presume the 9.10 method of [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page doesn't work? [Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is another help page (for wireless) - looks like you've already tried some of it.

---

