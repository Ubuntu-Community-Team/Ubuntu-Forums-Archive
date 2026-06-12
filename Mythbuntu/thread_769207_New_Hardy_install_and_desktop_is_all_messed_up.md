---
title: "New Hardy install and desktop is all messed up"
date: 2008-04-26
forum: Mythbuntu
---

### Post by houstonbofh on 2008-04-26
Been in Ubuntu a while and got the new release to try Mythbuntu.  Now I know how new Windows users feel. :)

Intel E2180
Biostar T-Force P965
Nvidia 7300GS
WD 500 Gig SATA
Pinnacle PCTV Pro
Large Old CRT

1) Got bit by the "Hardy don't know old monitors" bug.  Easy to fix in Ubuntu, but tough to fix in Xfe...  Used the gnome monitor app in ssh...  Then selected a proper resolution, (1024x768) and it kinda works. but...

2) The system font is way small.  Every preference dialog I see has it set to 9, but it is like 2...

3) The login screen only shows a small corner?

I also created a new user, and the default settings are too small.  Any hints?  Or is this an xfe thing, and I am in the wrong forum?

---

### Post by houstonbofh on 2008-04-27
Not solved, but understood.  It is a X / Xfce issue.  Solution is not not use a undetected monitor, or hardcode X resolutions.  Still a problem in Gnome, but easier to workaround.

---

### Post by ajeannotte on 2008-04-29
my login screen fonts are way too small as well. 

ubuntu 8.04 (though i had this problem in 7.10 as well)
nVidia 8500GT
Samsung 32" TV, 1360x768

i'm lost. any help?

here's my xorg.conf if it helps.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

