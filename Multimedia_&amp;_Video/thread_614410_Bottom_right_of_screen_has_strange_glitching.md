---
title: "Bottom right of screen has strange glitching"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by checho4 on 2007-11-15
I have a very strange problem.  I don't know how or why, but the bottom right of my screen has two sets of four horizontal black bars, and the only way I know of to rid myself of them is to go into a console (alt+ctrl+F1) and come back to my KDE session.  They are gone for a while, but seem to come back every-so-often.

What are these black glitches?  How do I get rid of them?

I'm using a Dell Inspiron 1501 with an integrated ATI Radeon XPress on it.  I'm running Kubuntu Feisty 64-bit.

Any help is greatly appreciated!  Thank you!

---

### Post by clean97gti on 2007-11-16
I have the same problem under Gutsy 32bit running a Radeon X1300. The first time I noticed it was just after updating to the latest ATI drivers.
I tried rolling back but it hasn't helped. They seem to appear for me when watching a video on Youtube.

---

### Post by tenach on 2007-11-19
I too have the same problem, and am also using Gutsy 32bit.  I have an integrated Radeon Xpress 1100 (uses the Xpress 200 driver download from ati.amd.com)

Driver version: 8.42.3
OpenGL version: 2.0.6968 Release

In CCC I have everything at the lowest, and upon closing the CCC it seems to have made them dissapear.  I am sure they're going to come back, but it's a temporary relief.

EDIT: It seems to only show up after browsing the Internet with Firefox.

---

### Post by willie_wang on 2007-12-17
The following seems to have worked for me.

Edit your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```

then add the following line to your Device section:
```
	Option		"XAANoOffscreenPixmaps"	"true"
```

Just as an example, my finall Device section looks like this:
```
Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ati"
	Option		"XAANoOffscreenPixmaps"	"true"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection
```

I'd be interested to know if this has worked for anyone else, so if you've been successful/unsuccessful, please let me know. thanks!

Wil :)

---

### Post by tenach on 2008-03-19
Sorry for such a late reply; I have been battling with Windows and have come back to Ubuntu.  Your edit worked for me, thank you!

---

