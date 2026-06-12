---
title: "Wifi from a laptop"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by yodiggity25 on 2009-12-25
so i have a HP mini 110 net book that is  dual booted for ubuntu and windows. I was curious if there is anyway to broadcast wireless from my laptop. I have an iPod I would like to get wireless for. any idea's. any help would be very much appreciated

---

### Post by FuManShu on 2009-12-26
The HP Mini 110 has a Broadcom 4312 Chipset so it should be able to start and connect to an Ad-hoc network.  To do that, left click the network icon --> "Create New Wireless Network..." --> Choose a name for your Network and security settings and hit "Create".  Connect to this via your iPod and you will have an Ad-hoc set up, but you won't have internet. If you cannot successfully create the Ad-hoc network, try installing the b43-fwcutter package(sudo apt-get install b43-fwcutter) and try again.

Go [_[COLOR="Blue"]here[/COLOR]_]("https://help.ubuntu.com/community/Internet/ConnectionSharing") and follow the directions there to enable internet sharing over the network.  You will probably have to change the settings on the iPod to Static IP, which you can do through Settings --> WiFi --> press the arrow next to the Network you created earlier --> Tap Static and enter the adressess below.  You may not have to do this if you can follow the "Ubuntu 9.10 Method" defined in the link previously mentioned.  

This could potentially be a lot of work so you might want to look into buying a wireless router and simplifying this.  Let me know if you have issues.

---

### Post by yodiggity25 on 2010-01-03
Been looking forever but i can't find the network icon to create the new conection.

---

