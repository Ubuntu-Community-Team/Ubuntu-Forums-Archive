---
title: "Hamachi loses IP"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by pean on 2009-03-12
I've always used Hamachi between my computers,  but since I upgraded to Jaunty Jackalope I've been having some troubles.

It seems like right after Hamachi is done with start up and adding tunnels to all peers and starting all the keepalive stuff it loses it IP-config: leaving me with this:

```
ham0      Link encap:Ethernet  HWaddr 5e:cd:f3:2a:21:34  
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:66 (66.0 B)  TX bytes:2103 (2.1 KB)

```

Previously this:
```
ham0      Link encap:Ethernet  HWaddr 5e:cd:f3:2a:21:34  
          inet addr:5.56.205.186  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:1707 (1.7 KB)
```


Any ideas anyone?

Can't see anything useful (to me) in the debug output.

I'm feeling kind of desperate, I'm going away on a trip in a couple of days and I need access to my office computer to be able to work when I'm away.

---

