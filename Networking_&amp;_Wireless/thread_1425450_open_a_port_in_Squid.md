---
title: "open a port in Squid"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by U-boy on 2010-03-09
Hi there,

A user from LAN need to connect to web-site of bank and he uses 4443 port. So it seems I need to open the port. I add this to squid.conf. 

acl Safe_ports port 4443 # bank client
bla bla bla
http_access deny !Safe_ports

But it doesn't work. What else I need to do?

---

### Post by Barriehie on 2010-03-09
Is the port allowed via your iptables???

---

### Post by U-boy on 2010-03-09
> Is the port allowed via your iptables???

No I don't think so. Because I didn't do anything with iptables.
So as I understood the port must be allowed via iptables, right?
How do I do this?

---

### Post by Barriehie on 2010-03-09
> **U-boy said:**
> No I don't think so. Because I didn't do anything with iptables.
So as I understood the port must be allowed via iptables, right?
How do I do this?

Okay, first off it's been 2+ years since I've configured mine so use at your own risk.  At least take a peek at the manpages!  :)

as root,
```

iptables -A -p tcp --dst bank-url --sport 4443 -j ACCEPT
```Before adding this rule I would back up your current iptables with **iptables-save** i.e.

as root,
```

iptables-save > *SomeFileName*
```to restore:
```

iptables-restore < *SomeFileName*
```

---

### Post by U-boy on 2010-03-09
It says bad argument 'tcp'.

---

### Post by Barriehie on 2010-03-09
> **U-boy said:**
> It says bad argument 'tcp'.

Try the rule again without the -p tcp part.

---

