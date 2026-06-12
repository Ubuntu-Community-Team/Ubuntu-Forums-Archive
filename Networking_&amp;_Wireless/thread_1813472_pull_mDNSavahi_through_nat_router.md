---
title: "pull mDNS/avahi through nat router"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by chele on 2011-07-27
I'm trying to figure out if it is possible to see avahi services through a nat. The wireless routers in use here (meraki) are locked down and we can't configure them.

Is there a way to configure computers on the nat side of the router to see avahi services broadcast on the other side?

---

### Post by bab1 on 2011-07-27
> **chele said:**
> I'm trying to figure out if it is possible to see avahi services through a nat. The wireless routers in use here (meraki) are locked down and we can't configure them.

Is there a way to configure computers on the nat side of the router to see avahi services broadcast on the other side?

Avahi services (mDNS) like all zeroconf protocols are for single subnet use only (i.e. they are link-local only).  By design they do not pass through routers (layer 3).

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/Zero_configuration_networking") for general information.

---

