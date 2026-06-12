---
title: "Force Chromium to use IPv6 when possible"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by SavageWolf on 2011-04-09
ipv6.google.com works, I use Teredo or something...

Uh, is there anyway to force Chromium to use always IPv6 on hosts that support it, such as xkcd?

---

### Post by lemming465 on 2011-04-10
Teredo has a moderately high connection failure rate and hideous latency, so if you don't have native IPv6, or near-native (6rd relay run by your ISP), it's pretty much only for masochists.

I'm not sure if there is a way to make Chromium prefer v6.  However, nearly all modern web browsers including Firefox and Chromium are using getaddrinfo(3) calls to resolve host names to a mixture of possible IPv4 and IPv6 addressses, and you can tune that behavior by adjusting */etc/gai.conf*.  I hvaen't had to adjust that myself, so I'm not sure exactly what you'd need to do.  A precendence line along the lines of```
precendence 2001:0::/32  25
``` might be a step in the direction of prefering Teredo addresses to legacy v4.

Any experts on /etg/gai.conf tuning want to chime in here and help us out?

---

