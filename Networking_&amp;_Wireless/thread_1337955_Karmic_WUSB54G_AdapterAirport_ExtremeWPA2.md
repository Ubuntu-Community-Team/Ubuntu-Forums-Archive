---
title: "Karmic: WUSB54G Adapter/Airport Extreme/WPA2"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by Zzarkc-20 on 2009-11-25
I am running Ubuntu 9.10. I as using the WUSB54G v4.0 USB Adapter to connect to a network run by an Apple Airport Extreme Base Station using WPA2 Encryption Security.

I can see the network, and I can even attempt to connect to it by typing in the password. The issue is that it never actually connects and it responds with "Wireless network: You are now disconnected."

I used to be able to connect a few versions back with Ubuntu using ndiswrapper, but I seem to be unable of finding a version of ndiswrapper to use with karmic, or at least to successfully install.

Any ideas are greatly appreciated! I've spent 2 days on the IRC chat with no success. I know it might be difficult to work with the base station, but my dual boot linux computer is definitely in the minority against every other OS in my house, so it's either drop linux or get it working. Thanks!

Geoff

---

### Post by raidoh on 2009-11-26
Your card is obviously working if you can detect networks, but your current driver likely only allows WEP or no encryption. I know that my Airport Extreme doesn't allow WEP, so if your driver can only support WEP, you'll be able to see the network but unable to connect. 

Have you installed wpa_supplicant? You might find this information useful over at the ndiswrapper wiki for your card. 
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB54G]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Linksys_WUSB54G")

---

