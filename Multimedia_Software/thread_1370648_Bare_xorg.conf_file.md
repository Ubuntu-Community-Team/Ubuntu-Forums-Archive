---
title: "Bare xorg.conf file"
date: 2010-01-02
forum: Multimedia Software
---

### Post by Mr. Matt on 2010-01-02
I'm trying to figure out how to increase the display resolution for my ASUS A7K laptop with an external Dell E193FP monitor.

I've done some searches where people suggest editing the xorg.conf file except mine is pretty bare and I don't know where to start editing.

This is the full file:

```
Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2560 768
	EndSubSection
EndSection

```

My laptop monitor can support up to 1440x900 and the Dell monitor can support 1280x1024 (currently the highest available setting is 1280x768).  If I go to Display Preferences, the two monitors are identified as "Unknown" and 'Dell 19"'.

What do I need to do to be able to access higher resolutions?

I'm running Ubuntu 9.10.

---

### Post by Jarige on 2010-01-02
If I'm not mistaken, I think you can try messing with the Virtual Display inside the xorg.conf file. You should be able to edit it with root rights.

First change the resolution of your second monitor to the highest possible, then change the xorg.conf file to match that resolution height. I do not know about this for sure, so don't blame me if things go bad.

---

### Post by barnex on 2010-01-02
```
man xorg.conf
``` has sometimes been helpful to me, though this manpage is a bit, well, long. Hope it helps.

Tip: backup your xorg.conf before editing. If X fails, you can always do a console login and restore it from the command line.

---

### Post by Mr. Matt on 2010-01-02
I ended up trying some things out as listed here:
 - [http://ubuntuforums.org/showpost.php?p=8560183&postcount=6](http://ubuntuforums.org/showpost.php?p=8560183&postcount=6)
 - [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I was able to get the external monitor resolution changed first and now I can increase my laptop resolution.  I'm not sure exactly what I did but it is working now.  Thanks.

---

