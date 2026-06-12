---
title: "Intel 5300 Wireless stops working after downloading 100 megs"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by outlawpsd on 2010-09-09
I need some help here as I am completely stumped.  I have a Dell E6500 with and Intel 5300 wireless agn card running Lucid x64.  Wireless works fine and speeds are great except when I download with either the browser or thru a torrent or even updates.  Once I get to around 100 megs in to the file wireless stops working and the only way to get it working again is to disconnect and reconnect to the AP.  I have installed the back ports and tried several other fixed to get this to work but nothing has helped.  Any advice at this point would be great.

One more note this happens on 2 other wireless routers that I have tried so I know that it's not limited to my Linksys.

---

### Post by outlawpsd on 2010-09-10
Anybody?  It's really annoying not being able to download anything  that is over 100 megs.  I can reproduce this at will if someone can tell me what information they need.

---

### Post by outlawpsd on 2010-09-10
Here is a little more info if it helps.  I tried to update Office 2007 to SP 2 in Crossover.  It ran until about 160 megs and stopped.  I then did an ifconfig and then I tried a simple ping.  I let it sit for 5 minutes and it never even gave a response.  I disconnect from my and and reconnect and I am back up and running.

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:f1:04:f8  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fef1:4f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:111992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168122099 (168.1 MB)  TX bytes:5053717 (5.0 MB)

computer@name:~$ ping [www.google.com](www.google.com)
^C
computer@name:~$ ping [www.google.com](www.google.com)
^C

---

### Post by outlawpsd on 2010-09-11
I read another article that suggested switching fro tkip to aes on the router for the security protocol.  This fixed the problem.  Does anyone know if there is a patch for tkip since I highly doubt I will be able to ask everyone to switch their security from tkip to aes.  Seriously does anyone know if the developers are working on this.  

Also how do I mark this post as sovled?

---

