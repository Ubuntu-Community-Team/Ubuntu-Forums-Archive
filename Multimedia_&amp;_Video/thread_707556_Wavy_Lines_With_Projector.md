---
title: "Wavy Lines With Projector"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by yochaigal on 2008-02-25
I'm using a Optoma EP719 projector and Gutsy Gibbon.

Essentially, when I plug in a 50ft or more VGA cable into my Nvidia GeForce 7600, and connect it to the vga port on the projector, the screen image looks clear and all but there are DISTINCT wavy lines running up and down the screen. They begin after the splashscreen (ubuntu logo) disappears.  
What's going on here?  Using a monitor (at 12ft, of course) this problem is also gone. 
When I  use a regular 12ft cable I do not have this problem.

I have tried adjusting the refresh rate on the linux box --- if I put it at 60, I get no output, if I use 70 or 75 the problem persists, and if I use 80 the problem goes away but is replaced by a constant, seizure inducing flicker.

Is it the cable length? If so that sucks, since this thing really needs to be far away.

Thanks

---

### Post by quarros on 2008-03-12
Hi! Your projector probably need an unusual refresh rate to work properly. I also had this problem and i solved it by putting some lines in my xorg.conf.

My xorg.conf are look like this:

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"XA7-19i"
	Option		"DPMS"
	Horizsync	28-80
	Vertrefresh	43-80
	ModeLine     "1280x1024-72" 133.5 1280 1368 1504 1728 1024 1031 1034 1073 +hsync +vsync
EndSection

Before I inserted this: 

ModeLine     "1280x1024-72" 133.5 1280 1368 1504 1728 1024 1031 1034 1073 +hsync +vsync
I wasnt able to modify my nvidia settings to 72hz but after that it workt like charm.

I hope that help!

---

### Post by yochaigal on 2008-03-12
Wow that really worked! I ended up using that resolution but sticking with 60hz.

Using the Nvidia-Settings manager is the only way it works, though.  

thanks!

by the way, the company I purchased the projector from suggested I buy vga amplifier; it had no effect.

Linux = 1

Common Knowledge = 0

---

