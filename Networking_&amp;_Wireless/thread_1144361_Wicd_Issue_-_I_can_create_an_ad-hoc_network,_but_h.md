---
title: "Wicd Issue - I can create an ad-hoc network, but host computer can't connect?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Noise... on 2009-04-30
I'm attempting to create an ad-hoc network on my laptop for my iPod Touch to connect to.

The issue is that the laptop itself is either disconnected from the network it's creating, or is connected at 0% - blocking anything from working. When it gets disconnected, and I attempt to reconnect, it gets stuck at "Obtaining IP Address..."

How can I fix this?

Here's the output from ifconfig and iwconfig, if they'll help.

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:80:f4:b2:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1926 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96300 (94.0 KB)  TX bytes:96300 (94.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:75.216.62.161  P-t-P:66.174.200.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:38573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:19914110 (18.9 MB)  TX bytes:3707551 (3.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:9f:86:35  
          inet addr:169.254.12.10  Bcast:169.254.12.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:fe9f:8635/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5275 (5.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3B-9F-86-35-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"wifi"  Nickname:""
          Mode:Ad-Hoc  Frequency:2.422 GHz  Cell: A2:00:11:CB:27:BB   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.

```


I saw one post mentioning setting a static IP of 192.168.0.1 onto wlan0. Will that fix this?

---

### Post by Noise... on 2009-04-30
Anyone?

---

### Post by Noise... on 2009-04-30
Bump.

---

### Post by Noise... on 2009-05-01
Up.

---

