---
title: "pdnsd caching problems"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by freelook on 2008-12-08
I'm using pdnsd with resolvconf.  For the most part this works great and it solves a lot of problems I was having with slow connections as I take my computer to different locations.

The problem is that it caches some domains for far too long.  Normally the domains should be cached for a long time.  The TTL is probably set pretty high because the servers' ip's don't change.  But as I mentioned, my computer is mobile, and I need it to resolve certain hosts differently depending on whether I'm inside that network or outside.  So I have one computer, server.domain.com, which resolves to something like 216.xxx.xxx.xxx, which is great, but when I'm internal to domain.com, I need the internal IP, 10.0.0.18.  

What should I do?  I would rather not specify that server.domain.com never be cached, and I don't want to turn off caching for all domains, nor do I want to clear the dns cache.

Ideally, pdnsd would have an option to determine that the search domain is domain.com, and decide to resolve those addresses directly instead of reading them from the cache.

What do y'all think?

---

### Post by freelook on 2009-01-04
I solved this by writing a script that checks the search domain.  If it's different from what it was, it will clear both the present and previous domains from the cache.

---

