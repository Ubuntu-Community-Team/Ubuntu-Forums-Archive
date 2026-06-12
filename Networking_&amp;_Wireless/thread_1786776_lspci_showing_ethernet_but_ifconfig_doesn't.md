---
title: "lspci showing ethernet but ifconfig doesn't"
date: 2011-06-20
forum: Networking &amp; Wireless
---

### Post by braghetto on 2011-06-20
Hi everyone! I fresh installed ubuntu 11.04 but there's immediatly a problem: ethernet is not recognized!

So, why lspci correctly lists the device?

[HTML]diego@HP:~$ lspci
.......
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)[/HTML]but ifconfig doesn't ??

[HTML]lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:960 (960.0 B)  Byte TX:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:50:0d:bd  
          indirizzo inet:157.27.176.42  Bcast:157.27.183.255  Maschera:255.255.248.0
          indirizzo inet6: fe80::219:d2ff:fe50:dbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:366293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189209 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:545831990 (545.8 MB)  Byte TX:17376950 (17.3 MB)
[/HTML]I can't understand what's the problem.
Thank you in advance!

---

### Post by Iowan on 2011-06-20
**ifconfig** will show only active connections - **ifconfig -a** *should* show all of them.
**lshw -C network** should also show some details.

---

