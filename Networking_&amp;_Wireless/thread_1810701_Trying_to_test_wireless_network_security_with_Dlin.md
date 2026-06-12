---
title: "Trying to test wireless network security with Dlink-DWA 140"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by UnBr34KaBl3 on 2011-07-23
I was gonna try to hack my own wireless network connection to check if its safe but there is something seriously wrong with the drivers.

Running "sudo airmon-ng start rausb0" gives the following result:

```

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
818	avahi-daemon
819	avahi-daemon
820	NetworkManager
1228	wpa_supplicant
1958	dhclient
Process with PID 1958 (dhclient) is running on interface wlan0


Interface	Chipset		Driver

wlan0		Unknown 		usb


```

It should say something else here in order to work I'm sure. Also, running airdump-ng never finds anything.

What should I do to get it to work or is it hopeless with this card?

---

