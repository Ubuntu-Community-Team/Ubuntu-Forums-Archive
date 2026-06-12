---
title: "I can't change the screen resolution"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by cazz on 2007-06-22
I have a computer that have "SIS 630 onboard video" and now I run 1024x768

But that is something very wrong here.

I run Xubuntu 6.06 and in Xfce graphic controlpanel it only show 800x600 and below but I have change the xorg.conf to only run in 1280x1024 (I want to see if the computer can run that)

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

```

why dont the Xfce run that I have write inside the xorg.conf file?

---

### Post by singedwings on 2007-06-22
Is your monitor being identified properly? You may need to specify the horizontal and vertical refresh rates.

What does it say in the monitor section of your xorg.conf?

---

### Post by NeilBlanchard on 2007-06-22
Greetings,

Using this command in a console:

> sudo dpkg-reconfigure -phigh xserver-xorg

and selecting the video card and the resolutions that you want to have listed (by using the Space Bar) solved this situation for me.

---

