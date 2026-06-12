---
title: "Linux-wlan-ng -&gt; 2 more adapters that work"
date: 2006-05-16
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2006-05-16
Just to post that two of my wireless usb adapters work with linux-wlan-ng (found in Synaptic)

> Asus Spacelink WL-140 Wireless LAN USB Adapter (11mbps/802.11b)
Corega Wireless LAN USB Stick-II (11mbps/802.11b)

Instructions for basic setup:
> 
Install linux-wlan-ng from repositories
Add the following 4 lines to the bottom of /etc/network/interfaces
> # The wireless network interface
auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
Enter the following in terminal:
> sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="" authtype=opensystem (for any within range) 
OR
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=(Your ESSID Here) authtype=opensystem
sudo iwconfig (to see your access point)
sudo dhclient wlan0

if you need WEP there are further steps I have yet to get to
[EDIT]word is, it's this simple:
> sudo iwconfig wlan0 key "insertkeyhere" (no quotes)
but then there is 64/128 bit encryption, a 13 or 26 character code to sort out too
HTH someone, somwhere :-)

---

