---
title: "Noob Question -- Network Issues"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by secno on 2009-03-30
Hello, I just bought an Acer Aspire One (a mini laptop with an 8.9" screen). I installed Ubuntu with no problems and was trying to get it to connect to wireless networks (Atheros is the maker of my card). I ran wifi locater, disabled the older drivers (blacklisting them).

That did not work, so I decided to do updates (292 total). When I rebooted, I found I could not connect using a UTP cable. I've tried various methods of connecting to the wired network, with no avail. I can ping my loopback (127.0.0.1), but not the default gateway. It says the media is disconnected. I am getting a green light on the LAN connector.

Help! Do I need to re-install Ubuntu?

---

### Post by Iowan on 2009-03-30
Did it make wireless work?  Check in */etc/NetworkManager/nm-system-settings.conf* - that's where Network Manager stores its settings.

---

### Post by secno on 2009-03-30
No.. no network connections are working.. even wired.. I'm going to reinstall this tomorrow.

---

