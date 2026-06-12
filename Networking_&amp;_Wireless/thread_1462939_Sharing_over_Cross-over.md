---
title: "Sharing over Cross-over"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by Hydrohs on 2010-04-26
So I'm trying to connect my Windows 7 machine to Ubuntu 9.10 to share files wired rather than wirelessly, which is much slower. With two Windows machines all I had to do was plug the cable in and browse to the IP address of one of the computers. Unsurprisingly it's not that simple in Ubuntu. When I plug the cable into my LAN port I'm never given an IP address, Ubuntu never connects even after clicking on Auto eth. Any suggestions here?

I am able to browse to shares over the wireless, so it's just a matter of getting this corssover to work.

---

### Post by Iowan on 2010-04-26
**sudo lshw -C network** should show information about your interfaces - including what driver(s) they use.

---

### Post by Hydrohs on 2010-04-26
I'm not using it right now so not able to give the results of that, but I can connect to a router perfectly fine.

---

