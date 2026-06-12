---
title: "freezing /etc/udev/rules.d/70-persistent-net.rules"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2011-02-11
When network cards are changed, the file /etc/udev/rules.d/70-persistent-net.rules ends up with the new ones added, but not always the right way.  In particular, the names given are not the expected ... e.g. they become eth2 and eth3 (in most cases, but not always).  I have seen other names given sometimes, such as eth4 and eth6 (although the networking didn't even work after this happened).

How can I make this "persistence" be more persistent, and always use the names eth0 and eth1 when there are 2 NICs in there?

---

