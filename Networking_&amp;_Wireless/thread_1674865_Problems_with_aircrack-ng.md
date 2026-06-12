---
title: "Problems with aircrack-ng"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by nafnaf on 2011-01-24
Pls help me with this problem:

[PHP]root@MRX:~# airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
8879    wpa_supplicant
10972    avahi-daemon
10973    avahi-daemon
11169    NetworkManager
11172    dhclient
Process with PID 11172 (dhclient) is running on interface wlan0


Interface    Chipset        Driver

wlan0        Unknown     rtl819xSE - [phy0]mon0: ERROR while getting interface flags: No such device

                (monitor mode enabled on mon0)
[/PHP]

I don't now how to fix this but aircrack don't work proper.

---

### Post by genocideZero on 2011-02-20
Yea I am having the same exact problem. 

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID     Name
1045    avahi-daemon
1051    avahi-daemon
1053    NetworkManager
1216    wpa_supplicant
8191    dhclient


Interface       Chipset         Driver

wlan0           Unknown         rtl819xSE - [phy0]mon0: ERROR while getting interface flags: No such device

                                (monitor mode enabled on mon0)

---

### Post by lisati on 2011-02-20
We don't support breaking into other people's networks without their permission here.

Thread closed.

---

