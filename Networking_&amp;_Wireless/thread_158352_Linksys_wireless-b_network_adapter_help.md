---
title: "Linksys wireless-b network adapter help"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by Y-town on 2006-04-11
I'm now using ubuntu server instead of the basic ubuntu. When i used the basic ubuntu i enabled my wireless network adapter by going to system>administration>network then i typed in my password and enabled my linksys wireless. But how do i do this on ubuntu server?

---

### Post by az on 2006-04-11
[QUOTE=Y-town]I'm now using ubuntu server instead of the basic ubuntu. When i used the basic ubuntu i enabled my wireless network adapter by going to system>administration>network then i typed in my password and enabled my linksys wireless. But how do i do this on ubuntu server?[/QUOTE]

Probably by adding this to your /etc/network/interfaces file:


sudo nano /etc/networking/interfaces

auto wlan0
inet iface wlan0 dhcp
wireless-mode managed
wireless-essid (your ssid)
wireless-key (your wep)


Save and exit and then run
sudo ifup wlan0

It should be brought up on boot, too.

---

### Post by Y-town on 2006-04-11
How can you find your wireless-essid (your ssid) and wireless-key (your wep)?

---

### Post by az on 2006-04-11
You set them in your wireless router (or access point).

---

