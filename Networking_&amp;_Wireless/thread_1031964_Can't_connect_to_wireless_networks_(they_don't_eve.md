---
title: "Can't connect to wireless networks (they don't even show) on broadcom wireless card"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by iPodVision on 2009-01-05
I can't pick up a signal with a broadcom wireless. Yes I'm right next to the router I know I'm going to have to install something. Just did a fresh install of ubuntu 8.04

---

### Post by tuxxy on 2009-01-05
Seems like your driver isn't correct or at least active, have you checked if its supported by default which doesn't look like it.  

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You would be advised to read the wifi ubuntu wiki page which includes lots of info and a troubleshooting process you could also try ndiswrapper as a last resort but it will all be included in the wiki heres the link

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by iPodVision on 2009-01-05
> **tuxxy said:**
> Seems like your driver isn't correct or at least active, have you checked if its supported by default which doesn't look like it.  

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You would be advised to read the wifi ubuntu wiki page which includes lots of info and a troubleshooting process you could also try ndiswrapper as a last resort but it will all be included in the wiki heres the link

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

-.- Thats a huge page, anything easier?

---

### Post by Ayuthia on 2009-01-06
You can first try to see if you can instal b43-fwcutter.  Try going to System->Administration->Hardware Drivers and select the Broadcom b43 option.  You will need to have a working internet connection in Ubuntu to make it work because it will need to download firmware informaiton that will help make the module work.

If it does not help, please let us know the make and model of your wireless card.  Go into the Terminal and type:
```
lspci -nn
```and look for the line that has Network Controller or Ethernet Controller.  Let us know what it is and we could help point you in the right direction.

---

