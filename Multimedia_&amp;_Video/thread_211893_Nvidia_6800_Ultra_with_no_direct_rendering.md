---
title: "Nvidia 6800 Ultra with no direct rendering?"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by simucal on 2006-07-09
I have the Nvidia 6800 Ultra... and I have installed and/use the "nvidia" drivers.  However, when I run games like ET  you can tell they are very slow.  Then, when I run the command:
glxinfo |grep direct

I get, "Direct Rendering: No"

This is my device in xorg.conf:
> Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option 		"RenderAccel" 		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

I'm presently running XGL/Compiz fine.. I dont see any slow downs with it, however, when I try to run Enemy Territory it is obvious it is slow.  How can I get direct rendering to work?

---

### Post by tseliot on 2006-07-09
Remove XGL (or disable it when you play games) and you will get direct rendering

---

### Post by alaijmw on 2006-07-09
I'm having the same issue, and you're right, it is XGL/Compiz. If I log out and do just a gnome session it works fine - but is there an actual fix that lets you run XGL and get direct rendering? If not, is there a way to disable XGL without logging out and changing the session?

Thanks

---

### Post by tseliot on 2006-07-09
> **alaijmw said:**
> I'm having the same issue, and you're right, it is XGL/Compiz. If I log out and do just a gnome session it works fine - but is there an actual fix that lets you run XGL and get direct rendering?
I wouldn't know but I guess you can ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)


> **alaijmw said:**
> If not, is there a way to disable XGL without logging out and changing the session?
That's very unlikely (take it as a no)

---

