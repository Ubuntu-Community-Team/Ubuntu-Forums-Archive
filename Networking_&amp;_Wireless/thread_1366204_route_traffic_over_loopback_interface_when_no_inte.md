---
title: "route traffic over loopback interface when no interfaces are active"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by baldydonald on 2009-12-28
Hi, 
Is it possible to route traffic for the local machine (192.168.0.14) over the loopback interface when no other interfaces are active?

I have tried 
  sudo route add -host 192.168.0.14 gw 127.0.0.1 dev lo
which adds the route just fine, but I can't ping 192.168.0.14...
There is only one route present in the tables (the one described).

Attempting to set a _default_ route to route all traffic over lo doesn't let me ping 192.168.0.14 either.

This is an Acer Revo 3600 running karmic (mythbuntu distro) 9.10 acting as a mythtv "appliance" - it is connected to the TV, and the local "frontend" wants to connect to the local machine via 192.168.0.14 (the backend is listening on 0.0.0.0 so that other remote frontends can also access it).
The Revo has a wired connection to a router, and when the router is powered up, everything is just fine (traffic is routed out to the router and back over eth0, I assume). However, because I want a low-power solution (the Revo draws about 20W), I'd like it to work as a stand-alone device even when the router is powered off.

Any thoughts or advice much appreciated!

Donald.

---

