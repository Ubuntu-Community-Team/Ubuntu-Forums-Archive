---
title: "The access point wifi on the laptop. Ubuntu 10.04"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by zhk_real on 2011-12-17
I know that topic was discussed more than once, but all the ways that are found on the internet, I have not helped.
There is a laptop, there is an Internet connection to pppoe, you must distribute it via wifi.
Tried a dozen different ways, none gave a result.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:21:9b:d3:41:0b  
          inet6 addr: fe80::221:9bff:fed3:410b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10263469 (10.2 MB)  TX bytes:768861 (768.8 KB)
          Interrupt:16 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3808 (3.8 KB)  TX bytes:3808 (3.8 KB)

ppp0      Link encap:&#1055;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083; PPP (Point-to-Point Protocol)  
          inet addr:79.135.207.236  P-t-P:172.16.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:7983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:9892684 (9.8 MB)  TX bytes:639836 (639.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:c8:80:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

ppp0      no wireless extensions.

```

In networks, and in Linux in general, I do not know too much, so explain to a less accessible as possible

Sorry if I have something configured wrong, I live in Ukraine and my English is not very high, so that the translator used

---

### Post by zhk_real on 2011-12-19
Can someone help me?

---

