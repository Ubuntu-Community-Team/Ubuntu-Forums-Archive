---
title: "Resolving .local domains"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by bensode on 2010-11-29
I'm finding that I can not resolve .local domains anywhere except with nslookup and found on the LucidLynx release notes that there is a problem with avahi causing this.  Although the avahi service is convenient for locating printers and such can anyone else tell me what other services/options will be impacted on a default installation of Ubuntu if I disable this service?  Thanks!

Bensode

---

### Post by bensode on 2010-11-30
Well so far the only things I've found affected by issuing sudo stop avahi-daemon is the Empathy losing "People nearby me" and network printer browsing.  Neither of which are a big deal to me but might be for others.

---

