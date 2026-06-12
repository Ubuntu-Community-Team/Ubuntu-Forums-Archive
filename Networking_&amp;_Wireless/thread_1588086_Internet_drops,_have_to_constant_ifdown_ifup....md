---
title: "Internet drops, have to constant ifdown ifup..."
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by morgue on 2010-10-04
Hey guys, 

We have a proxy running at work (Squid), so everyone goes through it... It's basically a server with Ubuntu. 

When the Internet drops, 99% of the time we have to "ifdown ifup" the network interface on it and the issue is resolved, the other 1% we have to restart the router.

We believe it's related to the interface because we get a dynamic IP from the ISP.

My question is, is there something we could do to make it so we don't have to constantly (~twice a week) 'ifdown ifup' the interfaces?

---

