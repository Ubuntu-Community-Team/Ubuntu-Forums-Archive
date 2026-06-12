---
title: "Connecting to AP via terminal with BSSID"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by N1nj4turtl3 on 2012-12-17
Hi!
I know how to connect to a wireless network via terminal with
> iwconfig wlan0 essid NETWORK key PASSWORD
but I'm wondering if there is a way to connect to a network while specifying a BSSID.

Something like
> iwconfig wlan0 bssid AP-MAC essid NETWORK key PASSWORD
That doesn't work, obviously.

I've tried googling to no avail, but I'm sure there's a way to do it. I can specify a BSSID in the network manager but I'm trying to do it via terminal.

The reason I ask is because there are two AP's with the same name and sometimes one overrides the other and I can't connect to the right one.

If someone knows how to do it I would much appreciate it.

---

### Post by chili555 on 2012-12-17
Please try:```
sudo iwconfig wlan0 essid NETWORK ap 00:60:1D:01:23:45  key PASSWORD 
```You can get the MAC address in:```
sudo iwlist wlan0 scan
```Read more in *man iwconfig*.

---

### Post by N1nj4turtl3 on 2012-12-17
Thank you sir!

Maybe I'll read the manual next time first  ;)

---

