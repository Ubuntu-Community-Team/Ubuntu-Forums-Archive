---
title: "Hostname Discrepancy"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Jester A. on 2006-07-12
Ok, this might not be a problem with Ubuntu, but being new to Linux I can't seem to figure out where else the problem might be:

My DSL modem/router seems to think my computer has a name ("Sandy") that I have never, ever seen anywhere else on our home network.

Except other times when it thinks my computer is called "Linda" -- which is in fact what this computer used to be called before I did a full and total install of Ubuntu 6.06 and gave my system the name "Brick". 

(and my router/modem thinks there are THREE "Linda"s sometimes)

Shouldn't "Brick" be the only thing that this computer is recognized as?  Both my /etc/hosts and /etc/hostname files only refer to "Brick".  Where are those other names coming from and how do I eliminate them.

Networking works fine on the surface, but I'm having bypassing NAT blocking with Azureus and I can't seem to successfully port forward through my router to my box so I'm thinking this hostname issue is the problem.  Thats why I'm asking.

THanks for any advice...

-- jester a.

---

### Post by tturrisi on 2006-07-12
Routers maintain a clients' table.  Try refreshing the table or delete unused clients in the table.

---

