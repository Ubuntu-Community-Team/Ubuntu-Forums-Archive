---
title: "Intel GMA 950 World of Warcraft buggy"
date: 2008-06-27
forum: Multimedia Software
---

### Post by xlink on 2008-06-27
(Ubuntu 8.04)

Hi,

Ive been trying to get World of Warcraft to work correctly on my eMachine T5088 pos but I cant seem to get it to work well. The game starts up perfectly, logs in perfectly. Sound is great. The only problem is that the terrain is really buggy. The floor and mountains have 0 texture. The whole floor is one color. I presume this is a driver problem.

I have tried a few things including running:
sudo apt-get install xserver-xorg-video-intel

as well as editing my xorg.conf file to the intel driver as and also tried the i810 driver with no luck.

I tried using: Driver        "i810"     in my Device but this brought my resolution down to 640x480; however, this fixed the World of Warcraft problem  (still, my resolution was REALLY crappy).

The following is what my xorg.conf file currently has:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"Intel"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option 		"AddARGBGLXVisuals" "True"
	Option 		"DisableGLXRootClipping" "True"
EndSection

Any help would be much appreciated.

---

### Post by Pjotr123 on 2008-06-27
This is a weak video card, not suitable for heavy gaming. You need an Nvidia for that.

Disabling visual effects may help a bit:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(nujmber 5 )

---

### Post by xlink on 2008-06-27
I dont think this is the problem. Ive read around various people that are using this card.

As an added note, I dont know exactly what happened but I got it working for a brief moment. It stopped working when I rebooted WoW.

I was playing around changing SET gxApi "opengl" to SET gxApi "d3d" and back and removing it all together and at one point it worked.

Its not working now tho, so I have no idea what to do.

Any suggestions please.

---

### Post by xlink on 2008-07-01
Im still having problems. Help please.

---

