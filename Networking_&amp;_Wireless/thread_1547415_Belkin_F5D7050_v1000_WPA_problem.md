---
title: "Belkin F5D7050 v1000 WPA problem"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by JohnMoriarty on 2010-08-06
I've recently moved and my desktop won't connect to the wireless network. My desktop happily connected to the network at my previous house (WEP secured) but won't connect to the network at my new address (WPA secured). (My phone and netbook both happily connect.) It is a shared house and I'm not in a position to change any of the network settings.

I can see the network and attempt to connect and am asked for WPA passphrase but it fails to connect.

desktop running Ubuntu 10.4, 2.6.32-24 kernel, x86_64

lsusb returns 
```
ID 050d:7050 Belkin Components F5D7050 ver 1000 wifi
```

iwconfig can see the interface wlan1, and it shows no connection.

so far I've been unale to find any solutions to the problem. Any ideas please?

John

---

### Post by wesleybishop on 2010-09-01
I am having a similar issue I can connect but once I do the internet does not work but it does on my windows pc and my psp 

[http://ubuntuforums.org/showthread.php?t=1565631](http://ubuntuforums.org/showthread.php?t=1565631)

---

### Post by MaindotC on 2010-09-01
There's a [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) that shows you steps for determining if your device is working and if you have the correct driver installed.  You may want to check the [List of Supported Wireless Cards](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and make sure you can use that version of the F5D7050.

---

