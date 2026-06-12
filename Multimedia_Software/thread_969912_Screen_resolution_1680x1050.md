---
title: "Screen resolution 1680x1050"
date: 2008-11-03
forum: Multimedia Software
---

### Post by Knad on 2008-11-03
Hey,

I cannot get ubuntu to display the correct resolution on my monitor (1680x1050). It does not seem to detect it correctly and will not display the option.

Graphics Card: Nvidia 6150se (onboard)
Driver: NVIDIA accelerated graphics driver (version 177) - Installed as recommended by System -> Administration -> Hardware Drivers
Monitor: LG Flatron Wide (L226WTQ - SF)
OS: Intrepid x64

Bug and detailed explanation: [293377]("https://bugs.launchpad.net/ubuntu/+bug/293377")

Any ideas?

Thanks

---

### Post by Knad on 2008-11-04
*bump*

Help!!!

---

### Post by eternalnewbee on 2008-11-04
Did you try it in: Main Menu > System > Preferences > Screen Resolution?
Is your Graphic Card enabled in: Main Menu > System > Administration > Hardware Drivers?

---

### Post by tlsarles on 2008-11-05
I recently had this same problem.
The modification that solved this for me was to make the following mods to my /etc/X11/xorg.conf file.

1. Adding the HorizSync Line. Your Values May Varry, and should be in the documentation for your monitor

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	30-82
EndSection

2. Adding Modes

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1680x1050" "800x600"
		ViewPort 0 0
	EndSubSection
EndSection


Hope this helps

---

