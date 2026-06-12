---
title: "Poor DVD Playback"
date: 2006-05-23
forum: Multimedia &amp; Video
---

### Post by ArchStanton on 2006-05-23
This is an extension from another thread I've posted:

[http://ubuntuforums.org/showthread.php?t=180700](http://ubuntuforums.org/showthread.php?t=180700)

However I think that this forum may be more appropriate for the problems I'm encountering now. I'm hoping to get some suggestions to tryout when I get home tonight. I'm using Dapper Drake 6.06

I've tried 2 DVD's so far, thats all I've had time for. One DVD (Star Wars EP1) won't work, I get the same error messages.

> Totem could not play 'dvd:///media/cdrom0'.
No URI handler implemented for "dvd".

OR

> Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart
Totem to be able to play this media.

Perhaps I may need to install regionset.

The other DVD worked, but the playback was horrible, and this is what concerns me the most. It displays one frame every 5 or 6 seconds, with no audio. I checked the drive for DMA access and it is on. I have a feeling that it's not using my video card to it's full potential because the screen saver has the same problem. My card is an older ATI All In Wonder, Rage 128 Pro.

Any suggestions?

---

### Post by Phlosten on 2006-05-23
My suggestion would be to assess what video drive you are using.
Check out your /etc/X11/xorg.conf file and see whether you are using the 'vesa' driver. If your X session is running with the vesa driver that would explain screensavers and dvd playback not running properly. The 'vesa' driver does not provide any acceleration.

---

### Post by ArchStanton on 2006-05-23
There is nothing in there about vesa. This is what it says about my video card.

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL D1226H"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 RF/SG AGP"
	Monitor		"DELL D1226H"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

---

### Post by ArchStanton on 2006-05-23
I reinstalled all of the non-free media formats making sure universe and multiverse were turned on, and then ran regionset. Everything is working now.

---

