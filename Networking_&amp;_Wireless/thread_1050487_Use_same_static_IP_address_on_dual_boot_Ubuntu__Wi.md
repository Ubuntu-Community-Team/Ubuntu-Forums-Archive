---
title: "Use same static IP address on dual boot Ubuntu / WinXP?"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by qprfact on 2009-01-25
Hi, on the basis that dual boot means that only one of the OS cane be working at any time, is is OK to assign the same static IP address in both the Ubuntu and Win XP partitions, or should I use separate for each?

Is there an "accepted standard" to follow?

Thanks in advance!

---

### Post by Kebabman on 2009-01-25
It is perfectly acceptable to use the same IP in all your OS's in that situation.

---

### Post by Iowan on 2009-01-25
Agreed - consider the IP as going with the "box" (although you need to configure it in each OS separately).  An alternative is to set up the DHCP server to issue a "static lease" based on MAC address.  Same result, but the OS would be set up go "get IP address automatically".  If you decide to change the address later, only the DHCP server would need to be changed.

---

