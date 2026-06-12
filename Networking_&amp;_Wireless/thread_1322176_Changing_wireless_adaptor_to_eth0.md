---
title: "Changing wireless adaptor to eth0"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Pink October on 2009-11-10
Is it possible at all to get a wireless adaptor showing as eth0?

---

### Post by t0mppa on 2009-11-10
Yes, you can overwrite logical names of the interfaces by editing */etc/udev/rules.d/70-persistent-net.rules*.

---

