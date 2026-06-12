---
title: "Gateway failover"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by Turbo Donkey on 2009-03-05
I have a few Ubuntu servers acting as Squid+Dansguardian proxies, which run like steam trains, never a flutter, even on older hardware...

One of my proxies has 2 available gateways on its lan, one is SDSL, and the other ADSL.  I want this proxy to be aware of both gateways, and failover from the ADSL to the SDSL if the ADSL becomes unresponsive.

The only caveat is that both gateways are on the same lan, so they will be on the same ethernet interface on the ubuntu box (eth0)

Is there a way I can configure this box to do gateway failover on the same ethernet interface?

:o)

---

