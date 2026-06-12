---
title: "pass real domain name to DNAT"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by W03L on 2009-06-15
Hi.
there is a site [www.example.com](www.example.com) with ip XXX.XXX.XXX.XXX (nslookup)
```
iptables -t nat -A PREROUTING -s 192.168.5.0/24 -d www.microsoft.com -j DNAT --to-destination XXX.XXX.XXX.XXX
```
this rule don't redirect [www.microsoft.com](www.microsoft.com) to [www.example.com](www.example.com)
it redirect to admin host XXX.XXX.XXX.XXX
i think that there are many domains on XXX.XXX.XXX.XXX

...DNAT --to-destination [www.example.com](www.example.com) - error detect
how can i do this?
(may be in some place need to point that XXX.XXX.XXX.XXX - is [www.example.com](www.example.com) in this context)

---

