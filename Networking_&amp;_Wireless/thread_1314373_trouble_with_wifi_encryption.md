---
title: "trouble with wifi encryption"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by lintypupik on 2009-11-04
I have an old Netgear PCMCIA wireless adapter. My wireless network uses WPA-Personal encryption. The network shows up, but when it askes for "Wireless Network Authentication Required" it does not list WPA-Personal as an option. It only lists WEP 40/128, WEP 128-bit passphrase, LEAP, and Dynamic WEP. What do I do to connect to the network?
 
If I go to System/Preferences/Network Connections I can create a network profile that has WPA-Personal, but I don't know how to force it to use that profile when connecting. It creates a new profile when I try to connect.

---

### Post by chili555 on 2009-11-04
Are you sure your old Netgear does WPA? Not every card does. Please stick it in the slot and do:```
sudo iwlist eth1 auth
```Substitute your interface, if it's not eth1. Does it say it does WPA, like this?> wlan0     Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current Authentication algorithm :
		open
		shared-key

---

