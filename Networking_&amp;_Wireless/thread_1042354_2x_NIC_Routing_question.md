---
title: "2x NIC Routing question"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by paulievox on 2009-01-17
I'm running Zoneminder (linux security camera platform) on an Intrepid 8.1 PC (xubuntu)
with two NIC cards.  I have 6 "IP" security cameras, which i placed
on their own network (10.0.1.x) with its own router.
The "Front Of House" connection lives on a 192.168.1.x network
with its own router.

Currently i'm bridging the connections on the Linux PC,
by setting the secondary NIC card up with a 10.0.1.x address,
but entering 192.168.1.1 for the gateway (the only way it seems
to work).

I found that by separating the cameras from my FOH connection,
i don't run into bandwidth problems (they're greedy devils).

Pardon my ignorance, but is there a more streamlined way to
set this up?  Should I include a static route on the 192.168.1.1 gateway
to the 10.0.1.x subnet?

((the PC needs to live on the FOH network so Apache can be accessed
by other FOH machines)).

---

