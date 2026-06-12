---
title: "Weird wireless problem"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by tanyeun on 2010-11-29
I used gnome network manager to connect to a free wireless internet in the airport
nm-applet showed connection established
and ifconfig looked like this :
> 
eth1   Link encap:Ethernet inet addr:10.224.134.31  
       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
       RX packets:1088 errors:0 dropped:0 overruns:0 frame:0
       TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 
       RX bytes:159964 (159.9 KB)  TX bytes:31255 (31.2 KB)

when I opened the browser, nothing showed up, eventually 
the browser told me "connection timed out"
and I couldn't ping out say [www.google.com](www.google.com)
I couldn't even ping the router 10.224.134.1

I am pretty sure my driver is working correctly, bcs I use wireless both at home and in school
any ideas?

thx,

David

---

### Post by uncaspi on 2010-11-29
this is not your router ip, but your card ip. You must probably add a route to the airport router. Look in this to see the routing table 
sudo route -n

if you don't have the default route named 0.0.0.0 or default you must add it.
sudo /sbin/route add default gw x.x.x.x eth1

where x.x.x.x is the gateway to the router.

---

