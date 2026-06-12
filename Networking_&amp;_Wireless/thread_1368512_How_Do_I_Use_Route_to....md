---
title: "How Do I Use Route to...?"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by noblow91 on 2009-12-30
I have a situation where I cannot stream media over the router connected to the internet. I got another router the other day and I keep it disconnected from the internet just so I can use it for my media streaming. I am wondering how to use route to set up my computer so that I can still access the internet with it without having to disconnect from from my streaming router...and vice versa.

I have a similar situation for my laptop as well, but I figure the answer will be the same for both

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0 
```

---

### Post by Iowan on 2009-12-30
More than one default gateway usually doesn't work. I suspect you only need the internet-connected router to be the default gateway.

---

### Post by noblow91 on 2009-12-31
I've tried removing the ones for my non-internet connect one, but as long as it remains plugged in to my computer I cant use the other router at all. 

I have found a better solution though. I have plugged my streaming router into the internet router. I can stream my media through my router and still access the internet. I don't have to worry about messing up my routing table either.:)

---

### Post by Iowan on 2009-12-31
Glad you found a workable solution.
(Thanks for marking the thread as [SOLVED]!)

---

