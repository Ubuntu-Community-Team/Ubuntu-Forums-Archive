---
title: "Set Ubuntu12 to prefer wireless over lan"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by zsugiart on 2013-07-04
hi all, 

any idea how to easily set my wireless connection as the preferred/default instead of the wired connection? 

I don't want to disable wired connection route to the net, or set it to "use this connection only for resources on its network"  I  want ubuntu to PREFER wlan0 over eth0
Which means, IF the wlan0 is not available, it will still try to use the eth0. but If wlan0 is available, should try to use it over eth0

I notice that if I run the route command when I disable the wired, it sets the default to be the wireless connection, but

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         pocketwifi.home 0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0

When I enable the wired conn, eth0 is preferred because. Seems this metric thing can be tweaked to adjust he weight of the connection

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0

But I'm not sure how to edit it properly in ubuntu12 - any pointer? I found a package called ifmetric, but when I try to run it it falls down on these error

$ ifmetric eth0 1
NETLINK: Packet too small or truncated! 40!=16!=1000

and manually hacking file doesn't seem the way to go anymore because networkManager is now in charge.

---

### Post by Cheesehead on 2013-07-06
> **zsugiart said:**
> any idea how to easily set my wireless connection as the preferred/default instead of the wired connection? 
...
Which means, IF the wlan0 is not available, it will still try to use the eth0. but If wlan0 is available, should try to use it over eth0


The system will, naturally, use the fastest connection to the gateway IP that it can find. That's almost always going to be the wired connection.
Is there a simple setting for such preference? No. Forcing a slower route while leaving both interfaces up is not an expected use case.

I suspect that you must script a custom solution.

---

