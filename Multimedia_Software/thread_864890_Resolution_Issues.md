---
title: "Resolution Issues"
date: 2008-07-20
forum: Multimedia Software
---

### Post by hasek522 on 2008-07-20
I have a view sonic E90f monitor and for the last few days have really been fighting trying to get ubuntu to display correctly.  I have continously tried to set the monitor up and select the correct resolution but it always reverts back to plug and play with the default resolution.  I have no idea what to do.

---

### Post by JagDragon on 2008-07-20
Edit the xorg.conf file and add the desired resolutions to the "Screen" section. To edit the file, type ```
gksu gedit /etc/X11/xorg.conf
```

In the file, you will find different "Sections". Find the part that looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
EndSection
```

And add a subsection of "Display" and edit it accordingly. You should end up with something like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24'
	SubSection "Display"
		Viewport  0 0
		Depth     24
		Modes     "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection
```

Save the file and exit. After that, to restart X, run ```
sudo /etc/init.d/gdm restart
```

---

