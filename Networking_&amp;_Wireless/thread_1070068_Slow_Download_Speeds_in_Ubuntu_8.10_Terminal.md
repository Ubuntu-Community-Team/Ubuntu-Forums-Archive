---
title: "Slow Download Speeds in Ubuntu 8.10 Terminal"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by s1lva16 on 2009-02-14
Hey everyone!

Im a very linux noob, (Installed Linux last night) and im just learning my ways around the terminal.


Aside from that, when i use the terminal to download packages/codecs, i get such slow downloading speeds! I get on average 60-130 Kb/s, but if i download like a big file off firefox, i can download at 1 mb + !!

So is their any tweak/port settings i need to change?

here is there results of ipconfig in the terminal:


eth0      Link encap:Ethernet  HWaddr 00:22:15:09:6c:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:4b:55:6f  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe4b:556f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24671565 (24.6 MB)  TX bytes:1593657 (1.5 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)


Can anyone please shed some guidance please?

---

### Post by 2hot6ft2 on 2009-02-14
> **s1lva16 said:**
> when i use the terminal to download packages/codecs, i get such slow downloading speeds! I get on average 60-130 Kb/s, but if i download like a big file off firefox, i can download at 1 mb + !!

Packages and codecs are small so it doesn't have time to get up to speed. It finishes and has to connect to the next d/l so restarting over and over makes it seem slow.

If you d/l the big file in a terminal it will be fast as well since it will have a chance to get up to speed before the d/l finishes.

d/l the small files in firefox and it will seem slow for the same reasons. It also depends on the servers it's getting the files from.

---

### Post by 2hot6ft2 on 2009-02-14
Also, have you had it find the best server for getting your updates and packages? It can make a big difference too.
System>Administration>Software Sources
click on the "Download From" choose "Other" then choose
"Select Best Server"
when it's done testing the servers click on "Choose Server" then Close and then Reload.

Now your updates and packages will come from the best server for YOU.

---

### Post by s1lva16 on 2009-02-14
> **2hot6ft2 said:**
> Packages and codecs are small so it doesn't have time to get up to speed. It finishes and has to connect to the next d/l so restarting over and over makes it seem slow.

If you d/l the big file in a terminal it will be fast as well since it will have a chance to get up to speed before the d/l finishes.

d/l the small files in firefox and it will seem slow for the same reasons. It also depends on the servers it's getting the files from.

Not true as i can download a 22mb file in firefox on a decent server and get 1 mb +, but a 22mb file in the terminal is always around 60-120kb/s

---

### Post by 2hot6ft2 on 2009-02-14
> **s1lva16 said:**
> Not true as i can download a 22mb file in firefox on a decent server and get 1 mb +, but a 22mb file in the terminal is always around 60-120kb/s
Really? The same file from the same server?

---

### Post by CaptConan on 2010-01-15
Thank you to 2hot6ft2 for that tip on finding a better server! A download that was scheduled for days now took seconds!

---

