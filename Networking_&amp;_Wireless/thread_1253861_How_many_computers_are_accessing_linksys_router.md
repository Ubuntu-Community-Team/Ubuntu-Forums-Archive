---
title: "How many computers are accessing linksys router?"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by helstreak on 2009-08-30
I have a linksys router and was wondering if it is possible to know how many computers are accessing the router?

Thanks

---

### Post by w00ly on 2009-08-30
any clients that get their IP via dhcp can be viewed in status -> local network -> dhcp clients table. If they manually specify their IP *and* are connected wirelessly, you can see them in wireless -> mac filter -> wireless client list (might have to enable mac filter to see the button). If they're connected via ethernet and manually specify their IP then I dont know. You could always install the DD-WRT firmware on it as it manages security and clients much better. All I have to do is click status -> lan to see all my clients and the bandwidth their using and everything

---

