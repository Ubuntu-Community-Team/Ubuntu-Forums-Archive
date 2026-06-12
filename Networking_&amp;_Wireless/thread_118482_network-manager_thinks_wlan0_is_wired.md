---
title: "network-manager thinks wlan0 is wired"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by hiadam on 2006-01-17
I just installed a recent Dapper release on a friend's old PC, which is equipped with a USB wireless card, the Hawking Tech HWU54G.  I had no problems installing ndiswrapper and the correct drivers, so ifconfig and iwconfig show a wlan0, iwlist returns several available access points and ifup connects the wlan0 to the best available access point.  wlan0 also shows up in the gnome network manager as a wireless network. 

My problem is that NetworkManager seems to think this is a wired connection.  So the nm-applet loads on startup and stays disconnected till I click on it, and then shows two wired connections:  wlan0 and eth0.  Choosing wlan0 causes it to correctly connect to the strongest available network vica DHCP but it doesn't allow me to see the available networks and choose one myself.  :-/   Has anyone else experienced this problem?

---

### Post by alime on 2006-02-28
I have, for some reason Network-Manager in dapper just shows my connection as wired even when it is not. I'm still able to use the Network Manger that came with Ubuntu but not the nm-applet program :(
"A"
im using a Centrino box.

---

