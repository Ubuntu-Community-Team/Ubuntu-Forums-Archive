---
title: "Ethernet, no connection"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by MajinSaha on 2009-06-16
I installed Wubi 9.04 recently on my Vista, laptop Toshiba Satellite M305D-S4829, 64 bit. In Vista I have troubles connecting to Internet through cable - it says "Local area connection" all the time, everywhere I'm trying to connect, although wireless works ok. In Ubuntu there's no connection through ethernet at all, even lights are not flashing. Again, wireless is good. I assume this has something to do with the driver in Ubuntu. If I do everything right, as long as it's not hardware problem, I believe it may be fixed, despite the problems in Vista. 
Please help ! What should I do ?

---

### Post by superprash2003 on 2009-06-16
so you have troubles with internet in vista too?? post output of** ifconfig** from the ubuntu termianl

---

### Post by MajinSaha on 2009-06-17
This is what I got. It has some russian language in it. If you need this completely in english, please let me know how to switch to another language.


lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          &#1042;&#1042;&#1045;&#1056;&#1061; LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:2b:69:f1
          inet addr:10.0.2.72  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fe2b:69f1/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2011 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2073 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000
          RX bytes:1942593 (1.9 MB)  TX bytes:384192 (384.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-2B-69-F1-00-00-00-00-00-00-00-00-00-00
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2009-06-27
post output of **iwconfig** as well... to know your wifi interfaces

---

### Post by MajinSaha on 2009-06-28
This is what I got.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by superprash2003 on 2009-06-30
well , this is sort of weird , eth0 pops up in your iwconfig output but not in your ifconfig output.. could you check your outputs again

---

