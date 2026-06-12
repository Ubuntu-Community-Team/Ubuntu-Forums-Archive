---
title: "No wireless connection after Hamachi2 installation"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by Zakard1989 on 2011-12-27
Hi everybody,
I have a Asus EeePC 1001PXD with Ubuntu 11.10.
The wireless connection worked always fine till I installed LogMeIn Hamachi2+haguichi. When I try to connect to my home wireless network it tries for a bunch of seconds and then says it disconneted. I tryed using an ethernet cable and both internet and hamachi2 worked fine. (I'm using it to write here)
Also if I "purge" logmein-hamachi I cannot use the wireless connection.
with code ifconfig: 
```
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:53:d7:d4  
          indirizzo inet:10.32.114.191  Bcast:10.32.119.255  Maschera:255.255.248.0
          indirizzo inet6: fe80::beae:c5ff:fe53:d7d4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2375 errors:0 dropped:0 overruns:0 carrier:1
          collisioni:0 txqueuelen:1000 
          Byte RX:1319381 (1.3 MB)  Byte TX:404533 (404.5 KB)
          Interrupt:45 

ham0      Link encap:Ethernet  HWaddr 7a:79:05:59:04:82  
          indirizzo inet:5.89.4.130  Bcast:5.255.255.255  Maschera:255.0.0.0
          indirizzo inet6: 2620:9b::559:482/96 Scope:Global
          indirizzo inet6: fe80::7879:5ff:fe59:482/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:500 
          Byte RX:0 (0.0 B)  Byte TX:14067 (14.0 KB)

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3492 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:276944 (276.9 KB)  Byte TX:276944 (276.9 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:df:7a:c3  
          indirizzo inet6: fe80::4a5d:60ff:fedf:7ac3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:23400 (23.4 KB)  Byte TX:52452 (52.4 KB)


```
with route -n
```
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.32.112.1     0.0.0.0         UG    0      0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
10.32.112.0     0.0.0.0         255.255.248.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

```
Any ideas?

---

