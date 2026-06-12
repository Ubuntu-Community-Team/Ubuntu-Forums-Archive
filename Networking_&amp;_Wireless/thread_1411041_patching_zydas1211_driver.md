---
title: "patching zydas1211 driver"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by andru183 on 2010-02-19
im following this guide:
[http://forum.aircrack-ng.org/index.php?topic=5334.0](http://forum.aircrack-ng.org/index.php?topic=5334.0)
to patch a zydas 1211 chipset but when all is done and i try to run airmon i get this:

andru@BOSS:~$ sudo airmon-ng start  -9 wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
954    avahi-daemon
957    avahi-daemon
1242    wpa_supplicant
14391    NetworkManager
15611    dhclient
Process with PID 15611 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        ZyDAS 1211    zd1211rw - [phy0]
mon0        ZyDAS 1211    zd1211rw - [phy0]
mon1        ZyDAS 1211    zd1211rw - [phy0]

if i follow the guide and use mon0 i get the exact same thing and it dose nothing else. i can kill dhclient and i get disconnected form the net and the others wont close even under sudo, any ideas how to get this to run?

---

