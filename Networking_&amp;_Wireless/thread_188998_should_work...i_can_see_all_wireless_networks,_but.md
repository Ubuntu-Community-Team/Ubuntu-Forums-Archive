---
title: "should work...i can see all wireless networks, but wont connect"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by barrmulio on 2006-06-04
i wanted to move my thread from [http://www.ubuntuforums.org/showthread.php?t=184244](http://www.ubuntuforums.org/showthread.php?t=184244) - mods, please delete the old thread since i had a fresh dapper install

started over with a fresh ubuntu dapper desktop install and formatted everything - so...
- Dapper updated to latest files, included network-manager, ndisgtk, ndiswrapper
- Dapper finds the device on boot !! auto-setup as eth2

- In network manager, i see all the wireless networks around me
- However, the link is never established, my router never sees the device even attempting to connect

- In ndisgtk, I can install my driver (prisma02) but it says no hardware present
- With ndiswrapper -l, I get a prisma02 invalid driver error
- In networking, the device is there, tried with both dhcp and static and nothing 

- Router is setup without encryption for easier troubleshooting, note that i tried some other non encrypted networks around me and I still can't connect. ](*,) 

I feel I must be close...

---

### Post by barrmulio on 2006-06-08
updating - since there are a lot of view but no answers...i guess it's a quirky card

the card is in this link
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D)

meaning it should work, I have ndisgtk now recognizing the card (hardware present  = Yes) but still can't connect.  I've run through about 6 different ndiswrapper wiki's but altho the power light is on, never any connectivity, and the route never sees any attempt to connect....

---

### Post by Joehome on 2006-06-08
I have 2 WLan cards that I have tried. Neither one works. Both worked before the upgrade. Any help is appreciated. Card is a Linksys WPC11 (Ver 3) and the router is a BEFW11S4.  Help! I miss the internet!!! :-) 

There is a great signal, but the DHCP dosent kick in. Looks like there is a lot of people with the same issue. Please help is typical users!! :-) 
-Joe

---

### Post by barrmulio on 2006-06-11
Joehome - have you tried yours on static ip?  Static didn't work for me, but seems to have worked for other folks on linksys equipment

---

