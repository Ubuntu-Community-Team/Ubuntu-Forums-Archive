---
title: "how can I disable kernel wifi drivers from command line so I can use madwifi?"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Thasp on 2009-01-25
As topic says.

Kernel drivers don't work for me like the madwifi did.

---

### Post by Sam Lars on 2009-01-25
Put the name of the kernel driver in
/etc/modprobe.d/blacklist
And the name of the driver you want to use in
/etc/modules

---

