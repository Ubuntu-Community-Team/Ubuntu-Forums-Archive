---
title: "Default connection"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by najsowy on 2010-05-03
Hello.
I have Ubuntu 9.10, and i have problem.
Look, I have something like this:

[http://www.iv.pl/images/27732208250113824612.png](http://www.iv.pl/images/27732208250113824612.png)

And i have no internet. There is both connections connected (wireless and wired), but eth0 is default, so i can't use internet.
When i disconnect wired i have this:

[http://iv.pl/images/86768372600895918170.png](http://iv.pl/images/86768372600895918170.png)

And i can surf the net.
So, my problem is:
"How change default connection from **eth0** to **wlan0**, and have both connected?"

IFCONFIG:
```
najsowy@najsowy-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:da:04:06  
          inet6 addr: fe80::224:1dff:feda:406/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11438 (11.4 KB)  TX bytes:38960 (38.9 KB)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:708 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55982 (55.9 KB)  TX bytes:55982 (55.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:e9:10:f8:c7  
          inet addr:10.0.67.195  Bcast:10.0.67.255  Mask:255.255.255.0
          inet6 addr: fe80::215:e9ff:fe10:f8c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24766195 (24.7 MB)  TX bytes:1171312 (1.1 MB)
          Interrupt:21 Memory:fddff000-fde00000 

najsowy@najsowy-desktop:~$
```Sorry for my english.
Please, help me.
The best way to do this is tell me in steps what i have to do.

Sorry, for my english again.
I'm polish.

---

### Post by najsowy on 2010-05-03
refresh

---

### Post by Iowan on 2010-05-03
Have you tried adjusting the "Routes..." settings under IPv4 Settings?

---

### Post by najsowy on 2010-05-04
That was that! Thanks!

Love ya!

---

