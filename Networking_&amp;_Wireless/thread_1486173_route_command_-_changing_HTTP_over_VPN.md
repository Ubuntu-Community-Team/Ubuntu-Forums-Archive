---
title: "route command - changing HTTP over VPN"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by Reactor5 on 2010-05-17
Ok, I'm trying to route traffic over port 3389 (RDP) over a VPN (PPP0) and everything else, or most of it, over my regular connection (WLAN0). I know that you use the route command to do this, but I'm a bit of a newbie when it comes to networking stuff. I've tried googling the route command, and can't find anything on what I'm trying to do. So can someone point me to either a basic route command walkthrough/article or tell me what kinds of things I need to add and remove from the routes to get this to work? I think I'm just having trouble getting started here. Thanks.

BTW, here's my route -n.

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.182.111.134  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```

And with the VPN connected:

```


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.182.111.134  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
70.182.111.134  192.168.1.1     255.255.255.255 UGH   0      0        0 wlan0
70.182.111.134  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

---

