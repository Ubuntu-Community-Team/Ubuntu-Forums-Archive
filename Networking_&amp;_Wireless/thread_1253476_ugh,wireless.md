---
title: "ugh,wireless?"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by Deicider on 2009-08-30
I was wondering , i have two routers; the current one is a wired with wireless capabilities and i have the previous router which can only be used as a wired, i wanted to use the only-wired router (change the settings) and use it as a current.
Know any ways to do that?

---

### Post by Iowan on 2009-08-30
*Should* be a "simple" matter of duplicating settings - particularly on the ISP side (authentication, etc). Hopefully, they don't have current router IP MAC address "locked in". If all your clients are DHCP, they *shouldn't* care if the IP range changes, but the router (DHCP server?) will need to pass along correct gateway, DNS servers, etc.

---

### Post by Deicider on 2009-08-30
Is there a way to check that?

---

### Post by Deicider on 2009-08-31
guess not :/

---

### Post by Iowan on 2009-08-31
> **Deicider said:**
> Is there a way to check that?Sorry for delay - sometimes I gotta work...
Check what - whether all clients are DHCP?  Yes, you could check network configuration on each machine - specifics depend on machine OS.
Check whether ISP has router MAC Address locked in? You'd probably need to give them a call.

---

