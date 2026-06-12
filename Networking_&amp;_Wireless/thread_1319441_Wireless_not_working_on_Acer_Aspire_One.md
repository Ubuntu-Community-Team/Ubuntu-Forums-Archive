---
title: "Wireless not working on Acer Aspire One"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by qprfact on 2009-11-08
Having previously run Jaunty and wireless worked perfectly, updated to Karmic. Maybe I should have been alerted during install when the network connection seemed to disappear, and when I re-started, wireless will no longer work.

I've tried reinstalling network manager and network manager gnome (via ethernet) - no joy. 

Also tried removing all lines from /etc/interfaces except:
auto lo
iface lo inet loopback

(seen on another post)

That didn't work either.

What else could I try please?

---

### Post by qprfact on 2009-11-09
It seemed that allowing the Acers to do the drive check on boot resolved this....

---

