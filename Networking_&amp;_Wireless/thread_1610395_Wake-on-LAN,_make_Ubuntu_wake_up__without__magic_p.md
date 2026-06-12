---
title: "Wake-on-LAN, make Ubuntu wake up _without_ magic packet"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by sunside on 2010-10-31
Hi folks,

I'm trying to set up my home server so that it sleeps most of the day (suspend to RAM) but wakes up as soon as someone tries to connect to it. Wake-on-LAN/MagicPacket works already, but since the server is behind a router and I need to access it from the internet, this isn't much of an option.

I configured the network interface to wake up on MagicPacket, as well as "physical activity" using ethtool, but still it won't wake up on, e.g. a ping.

Background info:
My server is running an Apache on ports 80 and 443, as well as SSH on standard 22. All three ports are forwarded by the router. The router itself, a WRT54GL, runs on the Tomato firmware which has a web frontend and also an integrated WOL tool. Since I need to access port 443 on the server, I configured the router to listen on port 4430.
While this basically works fine, my problem is that my university does not allow any access to non-standard ports. Because of that I cannot access the router's administration and consequently cannot wake up the server "manually". Since the server doesn't wake up on regular traffic, I'm locked out.

Any ideas?
-- Markus

Here's the output of ethtool:

```
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        [B]Supports Wake-on: pg
        Wake-on: pg[/B]
        Current message level: 0x0000003f (63)
        Link detected: yes
```

---

