---
title: "Problems with browser speed or DNS lookups in Karmic[karmic regression] all network a"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by sant on 2009-11-30
In Karmic, DNS lookups take a very long time with some routers, because glibc's DNS resolver tries to do IPv6 (AAAA) lookups even if there are no (non-loopback) IPv6 interfaces configured. Routers which do not repond to this cause the lookup to take 20 seconds (until the IPv6 query times out).
This is a [confirmed bug]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/417757?comments=all") in Karmic.It is a problem for many users.
Will be there an official fix?

---

### Post by hailtothethief on 2009-12-18
Bump.

This is a very irritating problem, and is just another straw in the haystack of troubles I've had since upgrading. I hope someone comes up with a solution quick.

---

