---
title: "Wireless works during install, then stops"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by mfenoglio on 2013-06-08
Hi, I've been trying to get this to work for the last 2 days (yes, I'm new to Linux). I installed Ubuntu Server 12.04, used eth0 as primary network. Once I got everything running I tried to enable wlan0 (that's my available interfaces). Wouldn't work. Managed to unblock, configured wpa_supplicant, changed /etc/network/interfaces with hidden SSID, etc. Nothing. Since I hadn't installed anything on the server yet, I decided to take the easy way out and re-install the whole thing and using the installer GUI to setup wlan0 as primary from the start. That worked, installer connected to AP and internet, installation completed just fine. Boot the server, no connection.  :-( 

Decided to take another step towards easy solution and installed Zentyal from scratch. Wireless selected as primary. Same issue, and it seems I'm back to square one, no matter what. Why does it work during install and then it stops?

BTW, wanted Ubuntu Server as my hardware is an old IBM T60 I had lying around.

---

### Post by praseodym on 2013-06-08
Sounds like a driver issue. Please show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/network/interfaces
rfkill list
sudo iwlist scan
cat /etc/resolv.conf
```

---

