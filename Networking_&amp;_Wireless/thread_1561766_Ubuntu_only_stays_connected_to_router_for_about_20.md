---
title: "Ubuntu only stays connected to router for about 20-30 minutes."
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by gohanssjn on 2010-08-26
Any ideas?

Computer is Dell Latitude XT, Ubuntu 10.04, using the Broadcom driver in the restricted hardware list.

Anyone seen something like this before?

---

### Post by Iowan on 2010-08-26
Only idea that comes to mind is probably a little far-fetched...
If you **sudo dhclient** - for how long is the lease?

---

### Post by gohanssjn on 2010-08-28
> **Iowan said:**
> Only idea that comes to mind is probably a little far-fetched...
If you **sudo dhclient** - for how long is the lease?

renewal in 38811 seconds.

---

### Post by coolman98 on 2010-08-28
what ? huh?

---

### Post by gohanssjn on 2010-08-28
> **coolman98 said:**
> what ? huh?

I connect.

I browse.

Connection dies.  If I try to reconnect, it sees the router, it never connects.  Just keeps flashing and never locking on.

---

