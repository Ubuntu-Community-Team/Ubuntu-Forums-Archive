---
title: "SNMP Proxy &amp; Caching Service"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by john_navarro on 2010-04-05
This really isn't a Ubuntu question although I use the OS on a daily basis. I'm looking for software which will act as a SNMP proxy/cache to minimize CPU loads on routers from the many SNMP polling devices on our network. So far I've been unable to find much on this. I'm hoping someone here may know of something that can do this.

Thank you,
John

DETAIL: My intent is to have a few machines poll the routers every 5 minutes and all other SNMP pollers will hit these caching boxes instead of the routers directly.

---

### Post by zehunter on 2012-10-11
Hi,

sorry to up a old message, but i have the same needs : a proxy/cache server that can get SNMP information (or receive them from trap but i prefer get) and keep them in memory.

then other server will do snmpget on the proxy/cache to get information many time without over load the real server ...

---

### Post by wildmanne39 on 2012-10-11
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

