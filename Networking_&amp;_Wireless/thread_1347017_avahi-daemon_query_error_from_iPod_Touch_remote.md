---
title: "avahi-daemon query error from iPod Touch remote"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by sahendrickson on 2009-12-05
It seems that avahi-daemon is not processing a query from iPod touch's iTunes remote. If I start iTunes while the iPod Touch remote is active all works well. However, if I turn on the iPod Touch remote after iTunes is already started, it cannot find iTunes and I get the following error in the syslog:

Dec  5 15:00:46 data avahi-daemon[21997]: Invalid query packet.
Dec  5 15:01:01 data avahi-daemon[21997]: last message repeated 2 times

Is anyone else having problems connecting to their iTunes library from an iPod touch that is using avahi-daemon?

Thanks,
-- Scott

---

### Post by Pooka on 2009-12-17
I don't use iTunes, but I am getting the same error message from avahi-daemon. After some tracking I figured it out that the query package was coming from my iPod. My guess is that it is an avahi issue, since it seems unlikely that the iPod is sending invalid mDNS packages (Apple wrote the mDNS spec, but who knows...).

I will keep trying to figure out what is going on and update this post if I find something relevant.

---

### Post by TheCat on 2009-12-30
I am getting the same error message with my iPhone 3G.

---

