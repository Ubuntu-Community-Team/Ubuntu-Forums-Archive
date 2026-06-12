---
title: "Unable to authenticate to home wifi"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by lolwhites on 2011-08-25
I acquired an old Compaq Evo laptop and installed Kubuntu on it. Bought a second hand wifi card, a DEXLAN IEEE802.11b (Having Googled to check it would work with Linux).

It detects wireless networks fine, and is able to connect to open ones, but I can't log into the home network with the password which works fine for Windows laptops.

I've tried every configuration of the router I can find, and followed the advice at [https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu#EasySteps](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu#EasySteps) but with no luck. It just asks for the password over and over again without connecting.

Can anyone offer further advice?

---

### Post by praseodym on 2011-08-25
Can you try to connect to your own network without/with WEP encryption instead (change encryption settings in your router interface)? If it works you can change encryption again.

Mixed WPA/WPA2-encryption often causes problems with the network-manager, better use WPA2-AES if possible.

---

### Post by lolwhites on 2011-08-26
One of the first things I did was reconfigure the router to WEP but it still didn't connect :(

---

### Post by praseodym on 2011-08-26
Do you use KDE 4.7 from the corresponding PPA? There were some troubles with that. System is up-to-date? Are both packages **network-manager-kde** and **plasma-widget-network-management** installed? Only one should be...

---

### Post by lolwhites on 2011-08-26
Using KDE 4.6, only network-manager-kde installed and system is up to date. When I have time I'm going to try wicd, according to the advice here: [http://askubuntu.com/questions/23391/unable-to-connect-to-wireless-internetwifi-through-kde-plasma-desktop](http://askubuntu.com/questions/23391/unable-to-connect-to-wireless-internetwifi-through-kde-plasma-desktop)

Edit - The only improvement is that the LED on the card actually flashes, but the password is rejected, both for WPA and WEP configurations.

---

### Post by lolwhites on 2011-08-27
Resolved by installing Ubuntu instead and setting my router to WEP. Not entirely happy as WEP is less secure.

---

