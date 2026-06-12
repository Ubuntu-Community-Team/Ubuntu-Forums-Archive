---
title: "is it ignoring xorg.conf? - 8.04"
date: 2008-05-02
forum: Multimedia Software
---

### Post by robotcontrolledbiodomes on 2008-05-02
Hello,

Today is my first day with Ubuntu. I'm running into a problem configuring xorg to work with my PCI radeon 9200se: it seems to be ignoring my xorg.conf file and just reverts to the VESA failsafe with low graphics. The only error in the Xorg log file is something about fonts; I see nothing that has to do with it even attempting to load the open source ati driver. I'm attempting to configure this with an LCD monitor that has a native 1280x768 resolution. Here's some relevant information -- let me know if i'm leaving out information

BTW I followed this guide: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

> **glxinfo |grep vendor:**
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)


> **lspci | grep VGA**
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
02:0b.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
> 
**/etc/X11/xorg.conf:**
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 9200SE"
	SubSection "Display"
		Depth	24
		Modes		"1280x768"	"1024x768"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Radeon 9200SE"
	Driver		"ati"
	Busid		"PCI:2:11:0"
	Option		"BusType"	"PCI"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
 	Screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
EndSection

Section "DRI"
	Mode	0666
EndSection

Xorg log file: [http://ubuntu.pastebin.com/f410b1df8](http://ubuntu.pastebin.com/f410b1df8)

Edit(solution): the problem was there was a grub option set to force Xorg to use the VESA driver. Press 'e' at the grub menu and delete the Xforcevesa from the line. Why was this automatically set? Not sure

---

### Post by Saint Angeles on 2008-05-02
not sure if this will help, but if you wanna try the proprietary "fglrx" driver, you could try my mini-tutorial:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

its worked on a bunch of computers i've worked on as well as a few other people here on the forums.

good luck on getting direct rendering enabled!

---

### Post by robotcontrolledbiodomes on 2008-05-02
I actually tried fglrx earlier tonight via EnvyNG, but experienced similar problems -- xorg reverting to VESA without any clues as to what is wrong. Also, ATI does not support their PCI cards anymore with their linux driver unfortunately, so I figured my best bet was with the open source driver. Any other ideas?

---

### Post by robotcontrolledbiodomes on 2008-05-02
Discovered what was wrong - details in the first post

---

### Post by Zorael on 2008-05-02
**/var/log/Xorg.0.log** contains X log output, so examine it for errors/post it here.

---

### Post by robotcontrolledbiodomes on 2008-05-02
Actually in my first post I went over the fact that the log file has no errors, and provided a link to it at the bottom of the post. But I figured out the problem, thanks.

---

