---
title: "Can not, for the life of me, share internet connection with Xbox 360"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by Xavier Oddmon on 2008-12-19
Okay, I have tried several attempts to share / bridge / do *anything* that will get my xbox to connect to my network through my laptop.

[LIST]
I've tried creating a bridge, following this guide: [http://www.linuxjournal.com/article/8172](http://www.linuxjournal.com/article/8172)
I've tried sharing, following this guide: [http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)
I've tried ICS in firestarter[/LIST]

All to no avail. My network is pretty straightforeward: 
phone line --> embarq DSL modem (192.168.2.1) --> netgear router (10.0.0.1) --> laptop (10.0.0.3) on wlan0 --> xbox 360 via eth0.

If I reboot my computer into windows XP home (dual boot), ics works perfectly. (Right click wireless network connection, enable sharing, local area connection 2 [l.a.c.1 is bluetooth for some reason]). (Windows working better than linux? That's something i'm not accustomed to!)

Now for some output:
```
chris@chris-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:92:4d:40:41  
          inet addr:10.8.16.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21d:92ff:fe4d:4041/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75384 (75.3 KB)  TX bytes:31490 (31.4 KB)
          Interrupt:249 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29880 (29.8 KB)  TX bytes:29880 (29.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:b7:b9:cf  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:feb7:b9cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2323427 (2.3 MB)  TX bytes:495794 (495.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-B7-B9-CF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'd provide more information if it is at all useful, please help!

Edit--
I forgot to mention what happens. The xbox fails at the network stage (the first stage). Additionally, if firestarter is running, when I hit test network connection on the xbox, the firestarter window shows that there is a 0.3kbps connection on eth0. And I enabled all traffic to eth0 in firestarter.

---

