---
title: "Can't find wifi"
date: 2006-05-21
forum: Networking &amp; Wireless
---

### Post by jic2000 on 2006-05-21
I have a wifi connection, with no proxy server or anything like that. I have a DHCP connection, but Ubuntu can't find my connection and won't get on the internet. Windows finds my connection fine, with no configuration or anything. Any help?

Also, unrelated, but Ubuntu won't let me use any resolution but 800 x 640. Again, Windows works fine with higher resolutions. Help?

---

### Post by spd106 on 2006-05-22
Try this wiki page [https://wiki.ubuntu.com/FixVideoResolutionHowto]("https://wiki.ubuntu.com/FixVideoResolutionHowto"), then try this one [https://wiki.ubuntu.com/WiFiHowto]("https://wiki.ubuntu.com/WiFiHowto").
Any questions or problems come back here and we'll help you out.
Good luck

---

### Post by jic2000 on 2006-05-22
Thanks for a speedy reply! The resolution page worked fine for me, but I can't figure out the wifi problem to save my life. I have two USB recievers. Neither one works for the internet, or shows up in the Network-admin program. When I type iwconfig in the Terminal with one of the recievers plugged in, the wifi0 connection shows up, but with the "no wireless extensions" message; with the other reciever, the wifi0 connection doesn't show up at all. I can't get the wireless-tools package it mentions, because I have no internet connection. I really can't figure out my problem; these are the only two recievers I have, hopefully there's a way to make them work?

---

### Post by spd106 on 2006-05-23
Can you identify the cards?
This wiki page has a useful list [https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards"), scroll down to the usb section.
As far as I know usb wifi support is still hit and miss, even more so than pci/pc cards.

---

