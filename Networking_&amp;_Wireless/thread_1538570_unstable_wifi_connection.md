---
title: "unstable wifi connection"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by vchibikov on 2010-07-25
Hi!

I've got a trouble with my wifi connection. It works well, but sometimes it lost. 

I can't find any logic, sometimes it works few days, sometimes disconnected in 30 minutes.

I've got router (it works stable, checked on other laptops) and vaio VPCCW laptop. 

my daemon logs:

> wpa_supplicant[1157]: Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxx' freq=2412 MHz)
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
NetworkManager: <info>  wlan0: link timed out.
wpa_supplicant[1157]: Authentication with xx:xx:xx:xx:xx:xx timed out.
wpa_supplicant[1157]: Failed to initiate AP scan.
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
wpa_supplicant[1157]: WPS-AP-AVAILABLE 

And these messages are repeated while network manager is trying to connect to router.

(I don't know what additional information you need)

Any ideas?
Thanks

---

