---
title: "?My Asus RT-N66U has /etc/static_routes"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by ecowan on 2013-06-05
I have an Asus RT-N66U router, which runs on Linux. I love it.
I'm curious, so I enabled its telnet interface and started looking around. I found a directory, /etc/static_routes -> /rom/etc/static_routes that has several lists with names like china_edu.conf, which are full of ip addresses like 'from all to 1.51.0.0/16.
What's that all about? Can someone shed some light?
Thanks. - Erny

---

### Post by varunendra on 2013-06-06
> **ecowan said:**
> I found a directory, /etc/static_routes -> /rom/etc/static_routes that has several lists with names like china_edu.conf, which are full of ip addresses like 'from all to 1.51.0.0/16.

It should also have something in front of the line, like "allow" or "block" or something similar. Or, the whole list itself can be a blacklist or whitelist to certain static routes.

"**from all to 1.51.0.0/16**" means "**All traffic** (from anywhere on your network) **to 1.51.0.0/16**" which is an IP range for "China Education and Research Network".

Now if it is an "allowed" rule or a whitelist, I obviously wouldn't approve it, because I wouldn't like all my traffic to go to somewhere I'm not intentionally connecting to.

However, since it is a router, it is more likely to be a part of a blacklist or a "block" rule (which would mean - "block all traffic to 1.51.0.0/16") as part of a security measure. But you should confirm that yourself.

---

