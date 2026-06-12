---
title: "Route issue"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by ichigo11 on 2012-01-27
Hi!

I'd like some help with a route issue, here the problem : I took a VPN 2 days ago, and I'd like that only certain IP destination (for instance 192.168.0.5) goes through the VPN and the other data traffic goes to my ISP connection directly.

So, I set the VPN in network-manager, he works like a charm. But he takes all the traffics when he is turn on. (for instance the browser traffic)

I saw that I must use route to do that, but I'm pretty noob ^^

Here the route -n before activate VPN :

```
kevin@kevin:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

And here the route -n when it turn on :

```
kevin@kevin:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
188.121.240.39  192.168.0.254   255.255.255.255 UGH   0      0        0 eth0
188.121.240.39  192.168.0.254   255.255.255.255 UGH   0      0        0 eth0
188.121.241.252 0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```

Thanks!
(PS : sorry for the mistakes, I'm french ^^)

---

