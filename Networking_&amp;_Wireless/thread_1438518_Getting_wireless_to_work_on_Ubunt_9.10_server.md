---
title: "Getting wireless to work on Ubunt 9.10 server"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by austclint on 2010-03-25
Hi

at the moment I run the code;
```
sudo ifconfig [interface] down
sudo dhclient -r [interface]
sudo ifconfig [interface] up
sudo iwconfig [interface] essid “ESSID_IN_QUOTES”
sudo iwconfig [interface] mode Managed
sudo dhclient [interface]
```

and this gets my network going fine

Could someone let me know how to set up /etc/network/interfaces to get it running on startup

Thanks

---

### Post by chili555 on 2010-03-25
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid “ESSID_IN_QUOTES”   [COLOR="Red"]<--it doesn't need to be in quotes unless it has a space in it[/COLOR]

```No encryption? My 13-year-old script-kiddie neighbor will be right over!

Managed is the default mode and ordinarily needn't be specified. Post back with any questions.

---

### Post by austclint on 2010-03-25
Thanks heaps, I will add the wpa-psk key soon... hopefully I will get it right and not have to reload the system like before :)

---

### Post by chili555 on 2010-03-25
WPA is a bit more complex but do-able. Post back if you need help.

---

