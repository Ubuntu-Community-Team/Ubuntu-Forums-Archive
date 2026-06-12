---
title: "TV out xorg.conf newbies and generic video cards"
date: 2010-11-08
forum: Multimedia Software
---

### Post by ReformedRicky on 2010-11-08
i have searched the forums and i can't seem to find an answer that suites my particular problem. 

i am using Mythbuntu 10.04 (new to linux) i have a PlixQ (by ricavision) perl the company seems to have gone under. the drivers were available on their website in the past but now the links/phone numbers/e-mails don't work. i open up my computer and it seems to be an AOpen video card it is not shown on the Aopen website. however i found it for sale [http://goods.ruten.com.tw/item/show?11081213312778]("http://goods.ruten.com.tw/item/show?11081213312778") here 

the card has a DVI slot an S-video and a plug in to get Component funtionality. 

i can use the DVI with a monitor, i can use the S-Video (but it is lower quality) but if i use the component all i get is a Black a White screen (only the green plug works) i've looked into the xorg.conf file but i know little about it and mine is very generic. 

```
"Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

is this a driver problem or a xorg.conf problem? should i just play around installing random drivers to get the 3D acceleration i need? 

i tried adding random functions to the xorg.conf file but i don't know if this is pointless if i have the wrong driver. please help. :confused:

---

### Post by ReformedRicky on 2010-11-13
:-k](*,)

---

