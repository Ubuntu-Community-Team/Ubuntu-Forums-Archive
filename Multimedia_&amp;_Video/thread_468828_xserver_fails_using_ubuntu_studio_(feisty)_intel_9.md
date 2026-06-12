---
title: "xserver fails using ubuntu studio (feisty) intel 945GM"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by robbiesduck on 2007-06-09
i have an nec versa m160 latop ! its reasonably new and uses intel 945gm graphics but i cannot get ubuntu studio to load up, each time i try i get a message saying xserver failed ! i assume it is some kind of driver problem but i am quite a beginner so dont no !
any help would be very very much apreciated :p
thanks

---

### Post by josesanders on 2007-06-11
Have you already installed Ubuntu Studio, or are you just trying to start the live CD?  What error message do you get when xserver fails to start?  You should be able to see information about what went wrong.

One thing that I should mention, Ubuntu studio uses a special low latency kernal, and I've had some problems with display drivers not working right with it.  Do you necessarily need the low-latency kernal?

---

### Post by SEXCALIBUR on 2007-08-10
I've had this issue to, but it is in ubuntu studio 7.04. I suspect it is the same reason. I have come across a method to fix it. Since my intel 945GM is dual processor (i have a sticker that says intel centrino duo on my laptop) you just have to go through the error logs and jot down the i810 device that it says cant find or start. In my case it was PCI:0:2:1.

So if you write that down, go to recovery mode from grub, go to /etc/X11/ and open up xorg.conf for edit. Then where it says :

Section "Device"
	Identifier	"i810"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
EndSection

just add the appropriate missing device, so you should get:

Section "Device"
	Identifier	"i810"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
EndSection

Section "Device"
	Identifier	"i810"
	Driver		"i810"
	BusID		"PCI:0:2:1"
	VideoRam	65536
EndSection

Remember, this is just my situation, you may not have exactly PCI:0:2:0/PCI:0:2:1 as the ones creating the problem. Where it says VideoRam 65535, you can probably change that to whatever you want.

All I have left is just getting the 1280 x 800 screen res that I use to have on windows (I blew it off my hard drive completely XD )

Vista spells Doombringer

---

