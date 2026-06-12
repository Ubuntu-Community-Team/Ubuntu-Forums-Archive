---
title: "Dual Monitors"
date: 2009-03-12
forum: Multimedia Software
---

### Post by Duffman3 on 2009-03-12
Im trying to set up a dual screen environment with screen 0 being my laptop and screen 1 being my TV so I can watch downloaded video on my TV.

My laptop is a Gateway mx6445.
I bought this to get video from laptop to TV.
[http://microcenter.com/single_product_results.phtml?product_id=0304242]("http://microcenter.com/single_product_results.phtml?product_id=0304242")

And this is my Xorg.conf:

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Isn't it weird that the Xorg.conf is pretty much empty?

---

### Post by wolfen69 on 2009-03-12
[This]("https://wiki.ubuntu.com/DisplayConfigGTK") may help.

---

### Post by Reeman on 2009-03-12
If the device that you bought accepts the output of the computer then converts it to ntsc or pal then this has nothing to do with your xorg configuration. You will have to force the device to accept whatever your ubuntu install is capable of delivering from the laptop out. 

In system/preferences there should be a separate screen resolution setting for the vga out of your laptop...if this device control does not show more than one screen resolution then you need to find out what chipset is on the Gateway and whether or not the laptop vga out is supported for that particular chipset. Chances are that if it is not supported by default with Ubuntu then it is a "proprietary driver" ...which can be a pita. 

Sometimes the VGA out of the laptop will be disabled in the bios unless activated by the " manufacture approved operating system " (the newspeak for it only works with Windows crap).... so Ubuntu will not even see it! Your laptop guide should tell you whether or not you have to configure things different for this device output to work. 

Gateway is a Microsoft centered product and has the annoying habit of hiding which onboard laptop chipsets they actually use on their website! It will take some research to find out wtf the laptop uses. 

If the laptop outputs to the vga at only the same resolution as the lcd laptop screen then try ctrl+alt++ or just cycle through your configured resolutions to see if the tv device suddenly comes to life at one of the Ubuntu pre-configured resolutions. Obviously the device does not talk back to the computer and tell X what it needs to work the way a monitor does.

Do not try unsupported resolution with the device for too long a period of time it might cause some problems with the device or the vga chip on the laptop.

---

### Post by Duffman3 on 2009-03-12
Ok I've done a ton of research over the last few hours. I'm now rather comfortable from a shell, and can hold my own writing in xorg.conf, yet still no solution. When I goto the screen resolution program there is no advanced tab and I can't seem to navigate to any of the dual screen options that are in the link above or the post above.

---

### Post by Duffman3 on 2009-03-12
Does anybody have any idea as to why I don't have advanced tab in the Screen Resolution menu?

---

