---
title: "RealPlayer wont rotate video output"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by voltsy on 2007-03-26
I like running Windows and linux with screen rotation, so that standard PDF "portrait" format documents can be viewed legibly in full screen mode, especially because a single PgDn keystroke jumps you to the next page: office productivity, here we come! ;-)

This has been easy in Windows with NVIDIA taskbar tool "nwiz" for a number of years. Once your nvidia accelerated driver is configured properly in xorg.conf, you can also have a permanent rotation applied to your Gnome (and KDE?) desktop GUI.

Here is part of my screen section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"DELL D1025HT"
	Option		"Rotate" "Right"
	Option 		"ExactModeTimingsDVI" "TRUE"
	Option		"ModeValidation"  "DPF-0: NoEdidDPFMaxSizeCheck, NoVesaModes"
	DefaultDepth	24
	SubSection "Display"

...as I recall, all of this is written by nvidia-xconfig except I added the line 
        Option "Rotate" "Right" 
...with my text editor. Apparently you can use nvidia-xconfig to rotate the GUI as well, but I have not tried this, and it probably cannot be done "on the fly" i.e. without shutting down your X.org first

My card is a GeForce4 MX 440 with 64 MB RAM, and the rotation is working fine. I even seem to have full 3D acceleration of my favourite screensaver - the GL accelerated "skyrocket" (magic!!)

The only fly in the ointment is RealPlayer 10.0.8.805 (GOLD), which now has a broken video stream. Actually the stream is still there, and can be partially viewed "unrotated"  by changing the view to full screen mode. But since I have my monitor standing on its left side, I now have to turn my head to the side to watch RealVideo clips. Help! before I get a sore neck!!

---

### Post by voltsy on 2007-03-26
I must also mention that CRT monitors without ventilation slots at the side may be prone to overheat when turned on their side. Take all precaution to prevent your valuable monitor, room, house, etc catching on fire ;-)

You must degauss every time you rotate a CRT monitor: it seems the earth's magnetic field, (and/or gravity effects on the internal mask) badly affect the screen's colour purity.

Don't drop it, don't sprain your back lifting this heavy awkward object. LCD owners have less weight problem, but more problem mounting the screen on a temporary stand to make it safe from falling or sliding off your desk.

---

