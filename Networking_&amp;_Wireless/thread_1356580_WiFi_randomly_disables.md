---
title: "WiFi randomly disables"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by GonzalitoUY on 2009-12-16
This is a litlle bug that I've encountered in some specifics cases:
first of all, my WiFi adapter is an crappy RTL8187b, that's present on my mini-pcie slot (laptop), but is internally detected as usb.
The issue happens when I'm not so far away from my router (15-20 mts), and most of the time can download at the best my ADSL connection can offer, but after some time (pretty random) the connection goes off, most specifically the adapter disables, as if someone turned the kill-switch.
The adapter appears as greyed out on the network manaager, and restarting networking(/etc/init.d/netowrking restart) doesn't help, only reboot the laptop.
Amy ideas of what may be the cause?
Got installed wireless backports on Karmic(somebody suggested me, that it could improve my WiFi experience), and the issue seems to be repeated when using Ktorrrent (at some distance from the router), or any intensive DL app (large files), and tried changing WiFi channel (doesn't seem to be hardware local or router, cuz Win7 on the same spot got no problem, and I'm the only one using Ubuntu back home)

---

