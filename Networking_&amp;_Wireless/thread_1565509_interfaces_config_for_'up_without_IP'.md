---
title: "interfaces config for 'up without IP'?"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by FliesLikeABrick on 2010-09-01
Hello all,

What is the best way to have a network interface brought up on boot, but without an IPv4 address?  In this specific case, I want the interface brought up so that IPv6 will autoconfigure, but don't want a static or DHCP IPv4 address configured on it.

I'm wondering if there is a way to do this without putting manual commands in /etc/rc.local or equivalent.

Related to this question is bringing it up with no v4 address but a statically configured IPv6 address (it doesn't look like you can put a 'iface eth0 inet6 static' clause in the interfaces file without having an 'iface eth0 inet static|dhcp' clause first).

(this all pertains to non-GUI installs, in case that changes anyone's suggestions)

---

