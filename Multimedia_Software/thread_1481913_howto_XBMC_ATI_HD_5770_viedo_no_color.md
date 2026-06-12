---
title: "howto XBMC ATI HD 5770 viedo no color"
date: 2010-05-13
forum: Multimedia Software
---

### Post by brdokoky on 2010-05-13
I was realy sad when I bought ATI HD 5770 . I tried XBMC and got result video no color, just black and white.
this is how to fix:
Of course install properly driver

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")


Than set in xorg.conf dri and dri2

gksudo gedit /etc/X11/xorg.conf

and add line in section ,,Module,,

load "dri"
load "dri2"

My xorg.conf is just :

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
        load    "dri"
        load    "dri2"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```

After start xbmc, and go to section system settings in XBMC . There go to ,,video,,
There adjust PLAYBACK
-RENDER METHOD = to  Basic Shaders (ARB)
-ADJUST Display refresh rate to match video
-Sync Playback to Dysplay

Now that's it . Have a fun :) :popcorn:

---

### Post by K.Mandla on 2010-05-13
Moved to Multimedia and Video.

---

### Post by KuruOujou on 2010-10-16
Thanks a ton for this! It really helped out. I know it's an old post, but it's one of the first that showed up in google for me in a search for "ubuntu xbmc black and white video". So for others who find this, I want to add these steps work with an ATI Radeon HD 4290, as well.

---

