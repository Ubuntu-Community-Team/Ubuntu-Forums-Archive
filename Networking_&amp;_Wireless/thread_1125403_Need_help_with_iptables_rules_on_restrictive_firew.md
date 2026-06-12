---
title: "Need help with iptables rules on restrictive firewall"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by JohnLM_the_Ghost on 2009-04-14
OK, so I'm building quite a restrictive firewall on my server box.

I need a bit help though... so I want to know how to deal with services (applications) what creates connections on dynamic port range.

So I have a firewall with all chains defaults to *-j DROP* (including OUTPUT).
And I've opened several port ranges for services.
Though I haven't really tried the firewall thoroughly, yet.

From what I can tell I need to track connections initiated from those service port-ranges, then "match and allow" them.
Or is there an other way?
iptables manpage is a bit cryptic and info from googling lacks detail.

So what is the right way making this work?

---

