---
title: "WLAN 9.10 BETA Asus 701 4G solved"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by Motomouse on 2009-10-03
I was not able to add a wireless connection (NMSettingWireless error). I intalled wicd instead of the network-manager according to this info [http://forums.geteasypeasy.com/viewtopic.php?f=12&t=2409&p=8302]("http://forums.geteasypeasy.com/viewtopic.php?f=12&t=2409&p=8302"). With wicd I was able to enter my wireless connection info, wlan up and running :-)

---

### Post by Motomouse on 2009-10-05
I had to reinvestigate my network-manager problems, because I wanted to connect via (Medion S4011) Huwai USB UMTS Stick. 

Two steps:
1.) I disabled access-list function in the router (WEP security still active). I do not know why this is necessary. Only that way the network-manager-applet showed the wireless network, allthough mac address is correct in the router access list.

2.) I did not enter the connection in the network-connections tool, but connected via the network-manager-applet (only possible after step one on my setup) and entered access key this way. WLAN up and running now

Gladly my Huwai USB UMTS Stick connected without problems.

9.10 netbook remix rocks so far on my Asus 701 G4, thanks to everybody contributing 

Regards

---

### Post by Iowan on 2009-10-05
Congrats on solving your connection problem! Are you aware that the [SOLVED] feature is back? (under Thread Tools) :P

---

