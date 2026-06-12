---
title: "Thinkpad T61 wireless [atheros card] instability with Jaunty"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by FatalChaos on 2009-04-28
Anyone else having instability with wireless internet with Jaunty? I've noticed that my wireless connection has been disconnecting far more often than it did with 8.10. I've also noticed that in areas with weaker wireless connections, the mass connecting/disconnecting i've been experiencing has caused my laptop to freeze up completely. I did use ubuntu tweak to change random non network related stuff, so I will do a clean reinstall at some point to confirm my experiences.

---

### Post by jcat1 on 2009-04-29
Having the same problem myself on t61.  Seems like my home network works fine, but at school the wireless connection is really unreliable.  At school the connection is authenticated based on MAC address while at home I'm using WPA2 (not sure if this makes any difference).

Any ideas?

---

### Post by FatalChaos on 2009-05-03
Apparenntly the problem is that the new ath0 wireless driver isn't quite ready for prime time. To fix this, go to system, admininstration, hardware drivers, and enable the alternate madwifi driver. This hsould fix everything.

---

