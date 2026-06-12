---
title: "trouble with ppp0 connection"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by n1wil on 2008-12-13
Hi,

I'm having the same problem as this person:
[http://ubuntuforums.org/showthread.php?t=632858](http://ubuntuforums.org/showthread.php?t=632858)

When the connection ppp0 starts the Network Manager still reports that there's no network connection, and Firefox always starts in offline mode when started.  Really annoying.

Also some network aware programs are not working properly due to this.  Here's a view of my ifconfig and route:

ifconfig:

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:166.214.91.227  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:2 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:94 (94.0 B)  TX bytes:157 (157.0 B)

Route:

john@d410:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0


Does anyone have a clue as to how to get the Network Manager to realize that I am actually connected?  I'm writing this post using this connection right now...   but it's damn annoying to have to tell Firefox and other programs that I really am connected to the internet.

I am using Ubuntu 8.04 (downgraded from 8.10 - clean install)  I downgraded because Intrepid did not work with my Sierra Wireless AT&T USBConnect 881 cellular modem.

Any help to fix this rather annoying problem would be most appreciated.  I tried to reply to the original thread referenced above but as an added annoyance, the original thread was locked and it appeared that the issue was still not solved.

Thanks,

John

---

