---
title: "iptables/ufw does anyone know how to..."
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by kingv on 2010-12-30
I was wondering if anyone knew how to open ports on a specific adapter with ufw or iptables..I'd prefer ufw but it'd be good to know both :) Thanks!!

---

### Post by PatchesTheCaveman on 2010-12-30
To open TCP port 25 (SMTP) on eth0 to all traffic:
```
ufw in on eth0 to any port 25 proto tcp
```

---

### Post by kingv on 2010-12-30
> **PatchesTheCaveman said:**
> To open TCP port 25 (SMTP) on eth0 to all traffic:
```
ufw in on eth0 to any port 25 proto tcp
```

You sir are the man! That's what I've been looking for! Thanks for the quick reply & happy holidays!:P

---

