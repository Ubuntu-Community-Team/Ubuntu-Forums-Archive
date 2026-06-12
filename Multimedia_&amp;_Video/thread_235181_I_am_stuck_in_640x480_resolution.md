---
title: "I am stuck in 640x480 resolution"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by notld223 on 2006-08-12
I just installed linux earlier today and after much work put in i finally got xords flgrx driver installed. Only problem is, is that i cant set my resolution above 640x480 and when i try to change it in aticonfig i get a segmentation fault message.

I'm running a dell dimension 2350, ati radeon 9250 and am not dual booting, i only have linux as of earlier today. proccesor speed is about 1.79Ghz I think etc. etc. 

help is appreciated,
   Nate

---

### Post by Greycloak on 2006-08-12
From a terminal window type:

```
sudo gedit /etc/X11/xorg.conf
```

Look for the "screen" section.  Then just add in other resolutions. Here is what the screen section of my xorg.conf looks like:

```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

See if that helps.

---

### Post by tseliot on 2006-08-13
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

