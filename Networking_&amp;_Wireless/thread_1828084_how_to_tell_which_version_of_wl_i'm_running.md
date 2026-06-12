---
title: "how to tell which version of wl i'm running?"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2011-08-18
I've been playing with my wl drivers, and I was wondering if there is an easy way to tell which version of wl is loaded?
THanks!
-J

---

### Post by bkratz on 2011-08-18
> **miatawnt2b said:**
> I've been playing with my wl drivers, and I was wondering if there is an easy way to tell which version of wl is loaded?
THanks!
-J


there may be an easier way but this will work



   sudo lshw -C network




and look at the driver version information presented. By the way that is a lowercase (L) in lshw.  It does take a few seconds for this command to operate. Capitalization is important and the sudo will require your password.

---

