---
title: "After upgrading to 12.10, some trackers in KTorrent won't connect"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2012-10-21
I'm using Kubuntu 12.10 (just upgraded) and that moved KTorrent up to version 4.2.1.  But now one private tracker won't connect at all, and just gives "Error: Invalid reponse from tracker".  Is anyone else having a problem like this with KTorrent 4.2.1?

Actually, version 4.2.1 seems to have problems with connecting to trackers in general, especially with a slow connection.  I've noticed that more than half of the time, perfectly valid trackers are erroring with timeouts, invalid data, could not resolve hostname, etc.  Of course, I do have many many torrents running, and a slow VPN, so a certain amount of timeouts are to be expected, but now well over half have trouble connecting, and one or two private trackers won't connect at ALL (and the "invalid response from tracker" error is confusing, because I don't know how a poor connection would cause that specific error).

I don't want to downgrade if I don't have to.

[img]http://www.pictureshack.us/images/90029_tracker.png[/img]

---

### Post by crabel on 2012-10-24
Disabling IPv6 helps for the moment: [http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

---

### Post by Stonecold1995 on 2012-10-24
> **crabel said:**
> Disabling IPv6 helps for the moment: [http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

I'm not using ipv6 in the first place.

---

### Post by Stonecold1995 on 2012-10-30
I upgraded to KTorrent 4.3 and it's working again.

---

