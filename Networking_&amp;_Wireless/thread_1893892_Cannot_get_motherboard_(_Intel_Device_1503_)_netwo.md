---
title: "Cannot get motherboard ( Intel Device 1503 ) network card to be recognized"
date: 2011-12-11
forum: Networking &amp; Wireless
---

### Post by ndelacova on 2011-12-11
I am having problems with the mother board supplie network card. lspci -v shows the network card and lshw shows that the network card is unclaimed.   How can I "claim" it?  I have downloaded the e1000e driver and built it (I have a e1000e.ko) file but I don't know what to do with it.  I tried modprob e1000e and it returned no error message.  I am at a loss.  Any help would be sincerely appreciated.

---

### Post by dandnsmith on 2011-12-11
The lspci -v should also show which kernel module is in use - is it the one you just loaded, or is there a different one needing to be removed first?

---

