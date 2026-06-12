---
title: "Help a fellow out"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by rdog157h on 2011-04-01
I have already searched for days on this issue and nothing I have read has worked, so dont reply with the google it response! I installed ubuntu 10.10 and cannot connect to the internet. I have a AWUS036h wireless adapter. Works great in windows, but when I boot into ubuntu 10.10 it connects to the network but I cannot access the net, I try to update drivers and it starts off but after about 30% it drops. I have tried the ipv6 disable commands, and every other thing I could find on google but still no luck! I have reset the router nothing works. Please help me out! Thanks in advance!

---

### Post by drewesq on 2011-04-01
What is the result of ifconfig, could you post your answer here?

---

### Post by rdog157h on 2011-04-01
This is ifconfig



eth0      Link encap:Ethernet  HWaddr 92:e6:ba:7d:44:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7984 (7.9 KB)  TX bytes:7984 (7.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:4f:30:12  
          inet addr:192.168.2.7 Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4689 (4.6 KB)  TX bytes:4659 (4.6 KB)

Thanks for the fast reply!

---

### Post by drewesq on 2011-04-01
Can you browse the web using an ethernet cable?
 
If so, connect up and try searching **proprietary drivers....**
 
**Or whatever the scan for hardware drivers is called..**

---

### Post by rdog157h on 2011-04-01
I do not have access to a wired connection.

---

### Post by Razorback on 2011-04-01
Your wireless has an IP address.  Does your wireless stay connected to your router or does it drop?  I had an issue where I could ping google.com but nothing else.  It was caused by not having my DNS servers setup in Network Manager.

---

### Post by rdog157h on 2011-04-01
Yes it does stay connected to the router, but when I open firefox it wont load. It also will start downloading the drivers and such but fails.

---

### Post by jawilljr on 2011-04-01
Since you have an IP Adress try this at the terminal:

```
ping 74.125.159.103
```The above pings google by using its IP.  If that works then try that same IP in Firefox's URL bar.  If they work then you know you have a DNS problem.

Jerry

---

### Post by rdog157h on 2011-04-01
Thanks, ill try that when I get home.

---

### Post by rdog157h on 2011-04-02
Ok I did the ping test and it only worked after I disconnected from the network and reconnected. It took me to google and I google searched something then when I clicked on the link it dropped, still showed connection to router but wouldnt work again till I reset connection. and again got to google but if I navigate away from it I get dropped. Does this sound like DNS problems? If so how do I fix it? Thanks

---

### Post by rdog157h on 2011-04-02
Anyone?

---

