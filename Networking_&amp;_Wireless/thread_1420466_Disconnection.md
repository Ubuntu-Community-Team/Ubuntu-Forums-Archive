---
title: "Disconnection"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by efranor on 2010-03-03
During connection to a wireless the connection disconnects after a few minutes. PS: it is not my box but a friends and we need help im currently trying to find out what network card he has.

---

### Post by Iowan on 2010-03-03
**sudo lshw -C network** should give plenty of details about the networking hardware. Is connection via Network Manager or */etc/network/interfaces*?

---

