---
title: "video turns black when window on left side of screen!"
date: 2008-07-30
forum: Multimedia Software
---

### Post by josvanr on 2008-07-30
hi

strange thing: after following the howto in this forum,
i can now play videos (avi, with mplayer, totem etc)
but i only see images when eg the totem window is *on the right 
side* of my screen. When i drag the window over to the left side of 
the screen, the movie turns black. (sound is still there). When 
i drag it back to the right side, picture appears again. This also
holds true for still images (when pushing still button). 

I have a PB easynote bg 46 with wide screen. Could this have something
todo with xinerama? 

jos

---

### Post by josvanr on 2008-07-30
video playing applications (totem/mplayer etc) turned
black when dragged to the left side of the screen. Cause: modes
of my widescreen laptop 
(Packard Bell EasyNote BG46-P-018 )
display were not detected 
automatically. The problem was solved by
adding the modes to xorg.conf:

Section "Screen"
	Identifier	"Screen-LVDS"
	Device		"Output-LVDS"
	Monitor		"Monitor-LVDS"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800"	"1024x768@60"	"1024x768"	"800x600"
	EndSubSection
EndSection

see also:

[http://cyril-ravat.homeip.net/blog/post/2008/01/05/Installation-dUbuntu-sur-un-portable-Packard-Bell-EasyNote-BG46-P-018-12-2/2](http://cyril-ravat.homeip.net/blog/post/2008/01/05/Installation-dUbuntu-sur-un-portable-Packard-Bell-EasyNote-BG46-P-018-12-2/2)

link also contains solution for sound problem

jos

---

