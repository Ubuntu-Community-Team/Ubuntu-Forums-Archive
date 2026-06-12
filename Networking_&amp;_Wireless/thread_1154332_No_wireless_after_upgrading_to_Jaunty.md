---
title: "No wireless after upgrading to Jaunty"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2009-05-09
I'm beyond frustrated, but kindly note that I recently had brain surgery and am very debilitated because of it.  Since I can't focus my eyes for more than a few minutes at a time, a few times a day, I'm left with very little opportunity to actually work on solving the problem. But I'm mad and frustrated anyway!

On the same HP laptop--a dv6000 with the dreaded Broadcom BCM43xx issue--that I had wireless working perfectly on with both Feisty and then Intrepid, it's simply not happening with Jaunty.  I remember being SO AMAZED at how easily I got it working when I upgraded to Intrepid--with Feisty I had to do the ndiswrapper thing, but with Intrepid all I did was activate the Broadcom B43 driver via "Hardware Drivers" and it worked. Of course I assumed it would be just as effortless with Jaunty. I was wrong.

Nothing's working. It shows that I have b43-fwcutter installed and that it's the newest version, but I cannot connect via wireless.  ifconfig yields:
```
eth0      Link encap:Ethernet  HWaddr 00:1b:24:66:9f:6f
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe66:9f6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1244014 (1.2 MB)  TX bytes:272624 (272.6 KB)
          Interrupt:20 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1960 (1.9 KB)  TX bytes:1960 (1.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:42:91:1b
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-42-91-1B-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Network Management shows:
```
WLAN Interface
Disconnected
```
(and, yes, it's enabled).

From within Network Management's entry for my wireless network, scan yields nothing.  Most of the time.  Every once in a blue moon it'll detect my--and my neighbors'--networks, but that's it. I can't actually connect.  Although Network Management shows that I have connected occasionally...but it must have been VERY fleeting, because I never even knew about it. Oh, my wireless light on the laptop is blue as it should be if wireless is working but, of course, it's not.

I've read as much as I can under my current circumstances but am left where I started, with no wireless.

Any ideas?  Advice?  Suggestions?

(It took me a span of four hours to write this. That's how bad my vision problems are. :( )

---

