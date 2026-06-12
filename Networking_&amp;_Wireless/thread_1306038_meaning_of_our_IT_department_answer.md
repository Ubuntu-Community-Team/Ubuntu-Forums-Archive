---
title: "meaning of our IT department answer"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2009-10-30
Can someone tell me (in layman's terms) what this answer from our IT department about the problem we were having with network speed means ?

[B][U]Too many collisions on main core router interface. 

Line speed was affected.[/U][/B]

---

### Post by Yoann Juet on 2009-10-30
hi,

>Too many collisions on main core router interface. 

it would mean there's a duplex mismatch between your router interface and another node (i.e. ethernet switch, another router, server ethernet card...). One node is running in the full-duplex while the other is in half-duplex mode. 

Check for speed and duplex autonegotiation. It should be activated on both nodes. Otherwise, you could set manually the speed and duplex mode on each interface card - should be 10/full-duplex or 100/full-duplex on both nodes -.

Regards,

---

