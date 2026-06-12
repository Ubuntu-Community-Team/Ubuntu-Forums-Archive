---
title: "Airmon-ng Not working"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by nizghat on 2011-02-03
Hi guyz, m using this software , and when i switch on my wireless device in monitor mode,
```
airmon-ng stop eth1
```
```
airmon-ng start eth1
```
it shows some error like some process are trying to stop airmon

Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID	Name
6936	NetworkManager
7187	avahi-daemon
7188	avahi-daemon
7435	wpa_supplicant
8348	dhclient
Process with PID 8348 (dhclient) is running on interface eth1


Interface	Chipset		Driver

eth1		Unknown 		wl (monitor mode enabled)


tell me how to fix this now

---

### Post by AlexQM on 2011-02-03
airmon-ng is used on wlanX, athX or wifiX. Not ethX as far as I can remember from using it so type "airmon-ng" to show what wireless devices are running.


Alex

---

