---
title: "Apparently 1920 + 1600 = 3840 in Ubuntu"
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by WalterDirt on 2006-02-14
Here are the relevant sections of my xorg:

Section "Screen"
	Identifier "Screen0"
	Device     "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor    "Dell 2405FPW"
	DefaultDepth     24
	Option	    "MetaModes" "1920x1200, 1600x1200"
	SubSection "Display"
		Depth     24
		Modes    "1920x1200"
	EndSubSection
EndSection

Section "Screen"	
	Identifier "Screen1"
	Device     "videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"

               #Viewport 0 0
		Depth     24
		Modes    "1600x1200"
	EndSubSection
EndSection

So why does my desktop actually go off to the side with 3840x1200. It's really annoying is all.

---

### Post by yusufk on 2007-02-07
Have you figured this one out ?

My resolution used to switch automatically depending on whether my 2nd monitor was connected or not but at some point it stopped and I now have to manually switch it every time I change from 2 to 1 or 1 to 2 monitors.

---

