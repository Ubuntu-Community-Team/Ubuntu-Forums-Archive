---
title: "how to find primary dns, secondary, and default router?"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by KruSuPhy on 2010-05-01
hi guys, im trying to open my NAT on my PS3, and it's asking for my primary DNS, secondary DNS, and default router. how will i find these on ubuntu? i got my ip and subnet mask, just need the other three.

---

### Post by Iowan on 2010-05-01
DNS entries are stored in */etc/resolv.conf*. The router is *probably* marked as "UG" on the bottom line in the results of **route -n** (run from a terminal).

---

