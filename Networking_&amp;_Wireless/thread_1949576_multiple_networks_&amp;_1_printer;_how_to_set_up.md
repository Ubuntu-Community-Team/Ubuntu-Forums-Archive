---
title: "multiple networks &amp; 1 printer; how to set up?"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by dreamquartz on 2012-03-30
We have set up 3 independent networks, but would like to setup a printer available to all.
Two networks (192.168.10.1 & 192.168.20.1) have their own router, and the 3rd (192.168.0.1) connects all to the internet. The connection is set up based on the WAN principle (see attachment).

We bought a HP color laserjet with WiFi recently, and would like to make it available to all.

My question is how to do that.

Thanks in advance,

Dream

---

### Post by dandnsmith on 2012-03-31
If I understand your configuration correctly, the simplest way is to connect the printer to the router which connects all to the internet.

To go any deeper, we'd need to discuss how you do the routing.

---

### Post by dreamquartz on 2012-03-31
> **dandnsmith said:**
> If I understand your configuration correctly, the simplest way is to connect the printer to the router which connects all to the internet.

To go any deeper, we'd need to discuss how you do the routing.

I connected the routers via WAN instead of LAN, which provides us with a high level of security. This indicates that when linked to one network, a system can not communicate with another network. At least that is the thought behind the set up.

As my attachment indicates, all routers have WiFi, and some equipment attached to them via WiFi.
However the routers are connected via wire.

Dream

---

### Post by dandnsmith on 2012-04-01
If you really did connect the routers via WAN, then you have a problem.
You're trying to use IP addresses in the private reserved ranges, which are, by convention, not routable.

Good luck

---

