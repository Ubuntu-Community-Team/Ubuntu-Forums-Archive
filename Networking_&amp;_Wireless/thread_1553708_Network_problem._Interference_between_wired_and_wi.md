---
title: "Network problem. Interference between wired and wireless network"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by Peppuzzo on 2010-08-15
I have got my problem with my network settings.
When I enable wired network connection (a switch between two desktops), I lose the wireless one (the link to my router and Internet gate). I mean the wireless connection is still enabled, but the computer is not able to exchange any bit.
More over I have difficulties in making this computer visible to the rest of the network.

---

### Post by Iowan on 2010-08-15
Check **route -n** I suspect the wired one becomes the default, and traffic goes that way. Also, **ifconfig -a** might reveal something - both interfaces *shouldn't* be in the same subnet...

---

