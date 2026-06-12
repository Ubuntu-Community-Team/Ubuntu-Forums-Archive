---
title: "rt2500 chipset Setting Wireless card to 54Mb"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by InDenial on 2005-12-19
Hi all,

I have installed my wireless network card (Sitecom WL-115). Great card btw.. but I have a problem. I followed the installation manual on:

[https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

The thing is that I do not run any gui. This system is gonna be streaming mp3's and nothing more. At the bottom of the page there is someone stating how to configure a file and move it to a certain folder. This was my only option since I could not use RaConfig2500 to configure the card. Everything works great now except for one thing. Below is my configuration file RT2500STA.dat
```
[Default]
CountryRegion=0
WirelessMode=0
TXBurst=0
TurboRate=0
BGProtection=0
ShortSlot=0
**TxRate=12** <- the readme file says that this means 54 Mb see below
PSMode=CAM
SSID=Badaboom
NetworkType=Infra
Channel=1
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=<key>
```
```
22. TxRate=value
   value
         0:     Auto
         1:     1 Mbps
         2:     2 Mbps
         3:     5.5 Mbps
         4:     11 Mbps
         5:     6  Mbps  //WirelessMode must be 0
         6:     9  Mbps  //WirelessMode must be 0
         7:     12 Mbps  //WirelessMode must be 0
         8:     18 Mbps  //WirelessMode must be 0
         9:     24 Mbps  //WirelessMode must be 0
        10:     36 Mbps  //WirelessMode must be 0
        11:     48 Mbps  //WirelessMode must be 0
        **12:     54 Mbps  //WirelessMode must be 0**
```
It just does not work. I have to set the TxRate manually using iwconfig ra0 rate 54M everytime after a reboot.

Anyone ever experienced this and knows a solution?

---

