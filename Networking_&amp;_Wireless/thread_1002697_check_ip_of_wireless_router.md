---
title: "check ip of wireless router"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by b-boy on 2008-12-05
how can i check ip of a wireless router

---

### Post by iponeverything on 2008-12-05
If you are connected via the wireless router:

```
route -n
```

the destination line starting with 0.0.0.0 will be your default route -- the gateway for that line will be your wireless routers address.

---

