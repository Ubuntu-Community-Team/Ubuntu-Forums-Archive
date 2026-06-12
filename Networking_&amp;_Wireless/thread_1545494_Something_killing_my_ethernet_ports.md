---
title: "Something killing my ethernet ports?"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by GerMulvey on 2010-08-03
I ahve the [same]("http://ubuntuforums.org/showthread.php?p=9673681") issue and it is not specific to ubuntu.
This leads me to the possibility it is the mobo lan ports. After install the lan is off. Booting to windows gives the same. Shutting down and powering off and on fixes the issue. 
But I still get the router showing orange over green occasionally but the lan works.

ASUS M4A785TD-V EVO
Realtek RTL8168D/8111D PCI-E Gigabit Ethernet Adapter

---

### Post by Iowan on 2010-08-03
Appending to a [SOLVED] post may not be the best way to get support - perhaps a separate thread will work better.
**sudo lshw -C network** will provide more information about your interface(s).

---

