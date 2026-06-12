---
title: "Realtek 8168B with r8168 driver - no cheksum offload?"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by bsh on 2009-01-04
hi
i am using an asus eeebox202 with realtek 8168b, ubuntu 8.04.1, changed the driver to r8168 (compiled form the realtek source code)
it woirks fine but it is still quite slow (~14mbyte/s).
checked the cheksum settings (sudo ethtool -k eth0), and everything is turned OFF.
ethtool won't turn on anything.
is this a realtek driver limitation?

---

### Post by Tom--d on 2009-01-04
Could be a driver issue.

EDIT: Its not wireless, is it xD


It should just work?
have you got the lastest kernel update on Ubuntu 8.04?

---

