---
title: "[SOLVED] 8.10 Wake On Lan  - No longer enabled"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by SirTrolle on 2008-12-03
Hi.

It seems that version 8.10 introduced a new feature, or an error, which is disabling Wake On Lan on my server.

It was working fine in 8.04, using a init.d script.
I have followed this guide without any luck: [http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex/]("http://sethbc.org/2008/10/12/wake-on-lan-and-the-intrepid-ibex/")

If I set the wol g feature, using ethtool direct, or using the script, the value changes from d to g.
But Ubuntu seems to clear this setting again when closing.

Output from ethtool, after enabling wol:

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x000000c5 (197)
        Link detected: yes

I have even tried using 3 other brands of networking cards  without any luck.

Any help would be appreciated.

- Kim -


**Update:** (30 minutes later...)

After reading [_this post_]("http://bugzilla.kernel.org/show_bug.cgi?id=9512"), I tried adding this line to the /etc/rc.local file:
ethtool -s eth0 wol g

This seems to have done the trick. :D

It seems like overkill to have both the startup script, and the rc.local code, but I will just leave it there for now.

Hopefully this can help someone else.

- Kim -

---

