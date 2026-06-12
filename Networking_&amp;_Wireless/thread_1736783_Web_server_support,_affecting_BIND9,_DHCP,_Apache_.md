---
title: "Web server support, affecting BIND9, DHCP, Apache HTTP, and ProFTP."
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by Lordestabia on 2011-04-22
I'm trying to set up a private web server on my machine, which will also be the main gateway for other computers/devices connecting to it to get to the internet. Services running is Apache HTTP, Proftp, Procmail (for internal mail from the machine), bind, bind9, and dhcp. My problem is though I can access my ip's without problems, I can only use the name based addresses ([www.ptysite.com]("http://www.ptysite.com"), and [www.ptydomain.com]("http://www.ptydomain.com")) when my internet connection is off. Tried to default it to my machine first, then to the internet, but it always, fails, and should it get going, my changes seems lost on reboot. Bounced through several websites looking for answers, including yours, and cannot find anything.

At the moment, it is localhost only (lo, lo:0..7) with addresses (127.0.0.1, and 192.168.10..80,1). Still need to add dhcp pools for eth, and Wlan0. And need assistance with this as well.

I'm relatively new to this kind of networking, and I'd appreciate any support you guys can provide. Any relevant config/log files will be provided on request should you need it.

Installed NIS client and daemons after this post was created.
Thank you in advance, and I hope you enjoy your day.

---

