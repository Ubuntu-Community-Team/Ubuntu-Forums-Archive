---
title: "If DHCP not available - fallback and start DHCP server"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by docblob on 2010-03-08
Hey Guys,

Am setting up a media server at the moment on a beagleboard and have a bit of query I am hoping you can help me solve. 

Currently I have my eth0 interface getting a DHCP address but at times the DHCP server will not be reachable. Sooo what I would like my server to do is if it cannot find a DHCP server assign a static address to eth0. Then start the DHCP service so it can then dish out some addresses.

How can I do this? Surely it is possible :)

Cheers, M

p.s. running 9.10 ubuntu arm port and have the DHCP service set up btw

---

### Post by Iowan on 2010-03-08
How likely is it that the "unreachable" DHCP server will _become_ reachable... and you'll have two servers handing out addresses?

---

### Post by docblob on 2010-03-08
On the whole if it does not detect a DHCP server at the start, another DHCP will not start or become visable

---

