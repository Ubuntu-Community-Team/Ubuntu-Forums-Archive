---
title: "ping broadcast address"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by lolek198787 on 2011-08-07
Hello,

I've got two host: first-10.10.10.1/24 and second-10.10.10.2/24 First host send ```
ping -b 10.10.10.255
```. I use Wireshark to monitor answer. But in Wireshark I see only echo request not echo replay(don't see any answer from second host). How change that?

---

### Post by larytet on 2012-07-16
Do ```
ifconfig
```
You get:
```
eth0      Link encap:Ethernet  HWaddr 00:24:e8:4a:33:e9  
          inet addr:137.167.20.96  Bcast:137.167.21.255  Mask:255.255.254.0
          inet6 addr: fe80::224:e8ff:fe4a:33e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47902179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14478477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:271055563 (271.0 MB)  TX bytes:459245673 (459.2 MB)
          Memory:fe6e0000-fe700000 
```

Pay attention to the broadcast address 137.167.21.255 do

Do ```
ping -b 137.167.21.255
```

---

