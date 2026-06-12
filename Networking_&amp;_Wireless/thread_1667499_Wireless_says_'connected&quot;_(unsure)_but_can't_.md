---
title: "Wireless says 'connected&quot;? (unsure) but can't surf anyway..."
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by pretty_whistle on 2011-01-14
I cannot connect via wireless because of an issue of some type.  I  filled in the info to 'connect to a hidden network' and when done the  wireless icon sort of blinks (for lack of a better description).  The  menu under it shows the hidden network SSID and the word "disconnect" is  right under it like it means I'm connected (that's what I meant in title when I said it shows "connected (unsure)"), but I'm not connected when I  try to surf.

I believe what the wireless icon is doing is showing it's trying to connect.  As it keeps trying I periodically get a window coming up that asks me for the WPA key.  It's already entered every time so I just hit 'connect' and it continues doing the same thing.

What is wrong?


I've installed the Ubuntu Desktop 10.10 next to Windows on the same laptop. 

My computer is a Compaq Presario CQ50 210US, laptop.

Hardware -
 Atheros AR5007 802.11b/g Wifi adapter
 

 Adapter type -
 Ethernet 802.3

I've already installed updates and was able to get my last issue resolved, which was the menu showing 'enable wireless' being grayed out, so I know that's ok.  Unless I'm missing some update(s) it didn't find.

Why doesn't it connect?

:confused:

---

### Post by Dhezballah on 2011-05-20
I have got the same problem with the same card, hopefully we can get some answers.

---

### Post by josephmills on 2011-05-20
Hi there could you please open your terminal (ctrl+alt+t) then type in ```
iwlist scan 
``` then paste here thanks

---

### Post by daxumaming on 2012-01-25
also have the same problem, still searching for possible answer on the interwebs. and I've already filed a bug report. [Bug #921123]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921123")

---

