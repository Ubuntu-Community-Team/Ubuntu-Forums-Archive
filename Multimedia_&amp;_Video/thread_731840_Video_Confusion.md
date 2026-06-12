---
title: "Video Confusion"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by Adman on 2008-03-22
Hi all

I have a NVidia GeForce 6600 GT graphics card and have been having some issues.  I considered the guide for driver installation, but just wanted to check if this is an appropriate step to take.

I am running Linux Mint 4.0 with the KDE pack.

When installing Ubuntu, I had to start in safe graphics mode, or else I'd get a funny black or blue screen with colored streaks which essentially rendered my computer useless.  I installed using the safe graphics mode, and everything was fine.  

I then tried a day later to change my xorg.conf (luckily, I had made a backup), simply to increase my monitor resolution.  Then the same thing happened with the distortion and absolutely no way to see KDE.   I got a console and restored the xorg.conf to the original.  

I'd like to know why this happens and also to know if installing the drivers is the appropriate step, or if I'm doing something wrong?

Thanks a lot

---

### Post by Sam Lars on 2008-03-22
What does your xorg.conf say?
I would definitely recommend installing the Nvidia drivers, probably through the Restricted Drivers manager.

---

### Post by cozmicharlie on 2008-03-22
I have the 6800 card.  I agree with Sam Lar - install the drivers.  While it is not the same card, below is my xorg.conf file you can use as a reference.  After you install the drivers, you will most likely only need to add to the resolutions part where it says "modes". You can just cut and paste from here or type it in.  I hope this helps

Section "Device"
	Identifier	"nVidia Corporation NV41.1 [GeForce 6800]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"UseFBDev"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-40
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV41.1 [GeForce 6800]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"

---

### Post by geezerone on 2008-04-06
Did you get the 6600 to work as I haven't managed to get my vanilla 6600 (not GT) to work. Would like to see compiz cube effects etc....

---

### Post by Adman on 2008-04-08
Hey :)

I managed to get things working - the problem was essentially based on having two monitors plugged in at the same time and, I guess, not knowing how to install...

The compiz cube effect is pretty awesome, runs fairly smoothly, so long as I don't have the VM machine eating all the RAM and running extra apps in Ubuntu ;)  How can I show it to you?

---

