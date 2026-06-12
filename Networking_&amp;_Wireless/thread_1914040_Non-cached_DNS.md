---
title: "Non-cached DNS"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by Pyraxic on 2012-01-23
Hello everyone,

I'm quite novice with Networking in Ubuntu. I would like to create a Non-cached DNS server based on Ubuntu and assign a public IP to it. We will be using the non-cached DNS into our firewall as primary DNS. What's the best way to approach it? Any help is appreciated!

---

### Post by Pyraxic on 2012-01-24
Bump

---

### Post by stefangr1 on 2012-01-24
> **Pyraxic said:**
> Hello everyone,

I'm quite novice with Networking in Ubuntu. I would like to create a Non-cached DNS server based on Ubuntu and assign a public IP to it. We will be using the non-cached DNS into our firewall as primary DNS. What's the best way to approach it? Any help is appreciated!

Bind 9 is the most used nameserver. I'm not entirely sure what you have in mind, but if you Google some tutorials things should work out.

---

### Post by SeijiSensei on 2012-01-24
Why would you want to disable caching on a nameserver?  The local cache speeds up the handling of queries and reduces network traffic.  The only time a cache poses a problem is when you change the upstream records for a domain for which the local server is not a slave.  In that case all you need to do is restart the nameserver to flush the cache.

---

