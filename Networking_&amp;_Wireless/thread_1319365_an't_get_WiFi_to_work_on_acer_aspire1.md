---
title: "an't get WiFi to work on acer aspire1"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by lprazdnik on 2009-11-08
Hello,
I have decided to install ubuntu9.1 on my acer aspire 1 netbook, however I can't get wireless to work. I tried installing the backports and enabling the ath5k module, but that doesn't work either. My wiFi card is Atheros AR5007, although when I type lspci it shows that my Wifi card is Atheros AR5001. Also when I type ifup wlan0, it says ignoring unknown interface wlan0=wlan0. Could this be the problem? Oh and, I've read a lot of forums posts and most of them mention that the atheros cards show up as ath0, but mine only shows up as wlan0. Do I need to reinstall anything? By the way, I am not using the UNR version because of accessibility reasons.

---

### Post by lprazdnik on 2009-11-09
Ok I decided to install madweifi-ng from svn, so as a result it is now ath0, but I still can't connect to any WiFi network via command line, or the gui. I even went as far as installing wicd and then reinstalling network-manager again.... By the way even though it says that it is ath0, it still says that the network card is Atheros ar5001.

---

