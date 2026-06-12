---
title: "WPA/WPA2 Only, no WPA Personal"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by boonie rat on 2011-05-13
Installed 11.04 Natty, hooked up to wired network, downloaded ndisgtk. Went to System>Administration>Windows Wireless Drivers. Did "Install New Driver" and installed Netgear wg511v2 drivers. Wireless Network Drivers window shows "wg511v2" Hardware present: yes.
Slid the adapter into the slot, waited for a few seconds, Clicked on the network icon on the panel and there are the wireless networks visible. Cool. Click on the appropriate network which is a WRT54G configured for connection via WPA/WPA2 personal, which BTW I am connected to on this system running 10.10, waited and,,, "Wireless Network Authentication Required" comes up showing WPA/WPA2 Enterprise with the only other option being "Dynamic WEP (802.1x) !!! Why for no WPA/WPA2 Personal ??!!!
I've tried to "Edit Connections" and enter the SSID, pick WPA/WPA2 personal but no connection, it only reverts back to ""Wireless Network Authentication Required" comes up showing WPA/WPA2 Enterprise with the only other option being "Dynamic WEP (802.1x)"

HHEEELLLPPPPP!!!!!!!!

---

### Post by Erubyr on 2011-09-09
Same problem here, but then for an Asus WL138G (used ndiswrapper to get it to work and everything seems to work now).

How do I get WPA & WPA2 Personal selected?

---

### Post by wildmanne39 on 2011-09-09
Hi, some drivers are limited in the way they can connect especially ndiswrapper, most people have better connectivity with just plain wpa2, but post the results of these commands and they will tell me what your driver is able to connect too.
```
nm-tool
```
```
sudo iwlist scan
```
Thank you

---

