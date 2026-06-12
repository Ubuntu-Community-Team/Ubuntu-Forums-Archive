---
title: "Help connecting via LAN, ethernet"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by Crownejules on 2009-06-02
I'm not an Ubuntu person, so trying to connect to the internet is turning into a huge issue.  I recently installed Ubuntu 9.04 on my Dell desktop computer, and now when I plug the ethernet cable in I get nothing...no connection...no recognized connection, just nothing.  

I've gone to the network manager, tried pinging different things and it "cannot find" whatever I put.  I open the network connections and it has "auto eth0" but it also says "never" by it.  

Right now the current configuration is wired cable modem-->wireless linksys modem-->to computer via ethernet cable.  I removed all password encryptions on the router in case that had something to do with the connection issue, but it still didn't help.

I have performed the following commands in "terminal":

ifconfig eth0:
link encap:ethernet  hwaddr 00:08:a1:24:3c:ae
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0  errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 frame:0
Collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:18 Base address:0xe800

---

### Post by Iowan on 2009-06-02
> **Crownejules said:**
> I'm not an Ubuntu person...Yet... ;)
I presume you're trying DHCP address? Check (also from a terminal) **dhclient eth0**.  It will likely report trying unsuccessfully several times, then going to sleep. [This]("http://ubuntuforums.org/showthread.php?t=1156441") is something you can try. It fixed my problem, so I naturally think it'll solve everyone's... :roll:

---

