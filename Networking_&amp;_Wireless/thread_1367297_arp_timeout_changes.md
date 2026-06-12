---
title: "arp timeout changes"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by peril on 2009-12-29
I'm trying to figure out how the following parameters interact on an ubuntu client (and this is really any linux client) - I would like to test failback default gateways 

i.e.
host 192.168.1.100

gw1 192.168.1.1
gw2 192.168.1.2

and I did some testing - just adding in the default gateways seems to do the trick - I'd like to know the math for the hold-down / expiriation timers. It looks like they are 

/proc/sys/net/ipv4/neigh/ethX/gc_stale_time

and 

/proc/sys/net/ipv4/neigh/ethX/locktime

are there any others that would affect the arp caching?

-Adrian

---

