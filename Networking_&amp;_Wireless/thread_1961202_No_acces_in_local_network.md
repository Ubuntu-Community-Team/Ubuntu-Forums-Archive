---
title: "No acces in local network"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by t1m88 on 2012-04-18
My network is setup as shown on the image below:


[IMG]http://img706.imageshack.us/img706/5702/netwerku.jpg[/IMG]



On my computer I can SSH into my phone and into the Apple tv.
On my phone I can only SSH into my computer, but not into the Apple tv.

Same problem for XBMC remote. On my computer I can acces the Apple tv on port 8080, but on my phone I can't acces the Apple tv with the local IP address.

My network settings:

eth0      Link encap:Ethernet  HWaddr 00:0e:2e:36:89:67  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe36:8967/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25895799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30351594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2792774272 (2.7 GB)  TX bytes:4191513500 (4.1 GB)
          Interrupt:20 Base address:0x1100 

eth1      Link encap:Ethernet  HWaddr 00:0f:fe:80:f8:0a  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe80:f80a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2366874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4102583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:170754028 (170.7 MB)  TX bytes:5429676339 (5.4 GB)
          Interrupt:17 

eth2      Link encap:Ethernet  HWaddr 00:08:a1:80:bf:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x1200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2991112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2991112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:419252875 (419.2 MB)  TX bytes:419252875 (419.2 MB)


How do I make sure that I can reach my Apple tv with my phone within the local network?

---

### Post by newbie-user on 2012-04-19
The problem is that your phone and the appletv are not in the same subnet. Your computer separates two different lan segments, 192.168.1.0/24 and 10.42.43.0/24. You can't communicate from one lan segment to another without setting up static routes.

I don't have an iphone, so I don't know if you can set static routes on it. If your phone were a linux computer instead, you could manually add a static route:

route add -net 10.42.43.0 netmask 255.255.255.0 gw 192.168.1.65 dev eth0


Basically what is happening is that your phone doesn't have directions (or a map) to get to the appletv.

---

### Post by t1m88 on 2012-05-03
On my jailbroken iPhone I've installed MobileTerminal in Cydia. Although it looks like a regular terminal, not all commands work. I've also installed Erica Utilities which added the possibility for a few more commands, but still I'm not able to add a static route. Also I've manually added some binairies from a 5 year old binkit, but I can't get them to work.
I'm in the wrong forum for questions about my iPhone, so I'll be back when I can set static routes on my iPhone.

---

### Post by t1m88 on 2012-06-18
Setting a static route on my iPhone isn't possible.

Is it possible to add a static route on the AppleTV? It has Crystalbuntu installed and I can acces it over SSH, so I guess it supports setting up a static route. If so what is the correct route I should add?

---

