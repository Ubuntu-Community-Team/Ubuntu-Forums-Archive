---
title: "portscan range of IP addresses to find my ssh server with its dynamic IP"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by earthpigg on 2009-11-05
my ssh server uses a pretty obscure port, but a dynamic IP.

the IP is always within a fairly predictable range, though, and the odds of someone else using that port within that limited range are very limited. (and ill switch ports if i discover someone in my "IP Address Neighborhood" using that port.)

lets say i wanted to check port 12345 on every IP address from 44.44.X.Y, where X is 40-45 and Y is anything from 1-255. 

how would i go about doing this? preferably via terminal.

---

### Post by DGortze380 on 2009-11-05
> **earthpigg said:**
> my ssh server uses a pretty obscure port, but a dynamic IP.

the IP is always within a fairly predictable range, though, and the odds of someone else using that port within that limited range are very limited. (and ill switch ports if i discover someone in my "IP Address Neighborhood" using that port.)

lets say i wanted to check port 12345 on every IP address from 44.44.X.Y, where X is 40-45 and Y is anything from 1-255. 

how would i go about doing this? preferably via terminal.

dyndns is a better solution. 

It may not be legal (or may violate your terms of use) to arbitrarily scan that IP range.

---

### Post by earthpigg on 2009-11-05
thanks for pointing that service out to me, got it all set up and working like a charm.

---

