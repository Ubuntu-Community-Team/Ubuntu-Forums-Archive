---
title: "2nd NIC disabling &amp; Public Network"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by umbernaut on 2011-04-18
I've had a tertiary Ubuntu box for some time that couldn't access the public gateway, but did fine private.  I finally decide to see why, and realized I had enabled the 2nd NIC some time back for a specific job, now not needed.  Suspecting this conflict, I ran "ifconfig eth1 down."  And sure enough, I could hit the public fine.  However, it came back as I pinged it from another box -- even though I had removed it from "interfaces" under /etc/network.

I even restarted networking with "/etc/init.d/networking restart" and it still comes back.

Please explain.  Is it caching the information now removed from interfaces?

---

