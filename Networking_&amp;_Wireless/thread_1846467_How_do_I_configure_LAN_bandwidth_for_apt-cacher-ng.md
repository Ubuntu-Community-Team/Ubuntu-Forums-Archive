---
title: "How do I configure LAN bandwidth for apt-cacher-ng?"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by r.osmanov on 2011-09-19
Hello. 

I've installed a server with apt-cacher-ng in our LAN, and changed URLs in /etc/apt/sources.list to point to *[http://192.168.1.42:3241](http://192.168.1.42:3241)* (the server) on client machines.

Following configuration instructions all finally worked. But clients download packages on about 40kB/sec, while it makes about 200kB/sec when downloading directly from Ubuntu mirror server(!).

I suspect LAN bandwidth should be significantly faster than 40kB/sec.

Regards.

---

