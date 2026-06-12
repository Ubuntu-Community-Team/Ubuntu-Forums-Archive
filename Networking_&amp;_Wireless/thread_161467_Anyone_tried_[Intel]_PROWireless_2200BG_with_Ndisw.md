---
title: "Anyone tried [Intel] PRO/Wireless 2200BG with Ndiswrapper??"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by mengqing on 2006-04-17
has anyone had any success with this card using ndiswrapper????...

I followed the ndiswrapper wiki... everything worked well until modprobe ndiswrapper which... crashed linux..i mean totally crashed.. had to cold boot..

thx

---

### Post by ruffneck on 2006-04-17
I have the the same card and I never needed to install Ndiswrapper to get it working correctly. Do you specifically want to get the card working with ndiswrapper for some reason? 

If not, just do a search for configuring "ipw 2200" For instance, if you're going to be connecting to a WPA wireless LAN check here:

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

good luck

---

### Post by bikeboy on 2006-04-17
I thought the drivers for that chipset were included in the kernel. "ipw2200" or something like that.

---

### Post by mengqing on 2006-04-17
ummm I am confused..

My notebook is Asus W5A with 915GM chipset..

For all these times I thought my wireless card is Intel Pro 2200GB.. even with lspci showed as 2200GB..

however I justed checked my windows setup cd and found out that the driver is for 2915ABG... I mean are these two the same??? I also checked on the web and W5A does have 2915ABG not 2200GB..

the reason I ask is because I followed all the solutions about setting up ipw2200 in this forum and it just didnt work...

---

### Post by YuHoo on 2006-04-17
Quote from the ipw2200: "This project was created by Intel to enable support for the Intel PRO/Wireless 2915ABG Network Connection and Intel PRO/Wireless 2200BG"
Also, if the newest drivers don't work for you, try the old stable drivers. I found that those have the best success rate and only miss a few really advanced features. The kernel also supports it "out of the box" but it uses older drivers that I've found do not work with anything but connectivity.

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
[http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)

---

