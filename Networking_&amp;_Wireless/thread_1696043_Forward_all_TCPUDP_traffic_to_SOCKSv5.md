---
title: "Forward all TCP/UDP traffic to SOCKSv5"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by canni on 2011-02-26
Is there a way to force forwarding all TCP/UDP traffic into SOCKSv5 connection?

I've ssh socks tunnel ssh -2 -qgND 8080 remote_host
and I would like to transparently tunnel all TCP/UDP connections through it (obviously with exception of tunnel connections itself)

How I can accomplish this?

---

