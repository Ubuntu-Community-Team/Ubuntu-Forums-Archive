---
title: "Problem Graphic card / SIS / Resolution / 3D"
date: 2009-03-20
forum: Multimedia Software
---

### Post by Kamikafre on 2009-03-20
Hi Everyone,

I've been trying for 4 days trying to configure Ubuntu, this is the second time I try to install Ubuntu, the first time wasn't fine but for patience (just install and install it), hope this second time could be to stay... What i wanted to say with this is that i'm totally noob...

I've been searching in lots of forums, google, everywhere and i have found some info, but the problem is i haven't found the ansers to my doubts/problems, so hope you can give me a hand to solve them...

[**SOLVED**]The first problem is the "resolution"(not sure this is the word in english), i can't pass from 1024x768, how to get the 11280x1024 or 1280x800 (it's supposed to be the right one to my pc) it's a mistery for me... I've tried to modify the xorg.conf (I've managed to get the 1024x768 that way), I've installed the drivers, and tried thousands of things to solve it... hope you can tell me where the problem could be...[**SOLVED**]

The 2nd problem is that i can't run the 3D, to smooth borders and all of thta. I've tried something about a gears on the console (Ok, I can see them), I've also tried a command where it should say yes to see if i can run the 3D (It said "Yes") but don't know what else to do....

This is my xorg.conf (not really mine, but modified on how it actually is):

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
Option "CalcAlgorithm" "XServerPool"
DisplaySize 304 190
HorizSync 30-50
Identifier "Monitor[0]"
ModelName "SAMSUNG LCD MONITOR"
Option "DPMS"
Option "PreferredMode" "1280x800"
VendorName "SEC"
VertRefresh 50-60
UseModes "Modes[0]"
EndSection

Section "Modes"
Identifier "Modes[0]"
EndSection

Section "Screen"
DefaultDepth 16
SubSection "Display"
Depth 15
Modes "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800" "1280x768" "1280x720" "1024x768" "1280x600" "1024x600" "800x600" "768x576" "640x480"
EndSubSection
Device "Device[0]"
Identifier "Screen[0]"
Monitor "Monitor[0]"
EndSection
```

These are my problems .... (until now...)


My laptop:

UBUNTU 8.10
laptop Ahtec XSW91
Intel® Core 2 Duo T6400 (2.00Ghz/2MB/FSB800/45nm/35w)
RAM: 2Gb
Graphic card:SIS® GMA M672® 256MB PCI Express

Thanks so much!!!

Cheers!

---

### Post by Kamikafre on 2009-03-21
Ok, I've managed to solve the problem of the resolution:
Download this drivers:
[http://launchpadlibrarian.net/20463699/xserver-video-sis671_ubuntu8.10-1_i386.deb](http://launchpadlibrarian.net/20463699/xserver-video-sis671_ubuntu8.10-1_i386.deb)

then go to a console and input this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It'll show a message that ther could be a problema and a backup has been done, just FYI, then, restart the X with Ctrl+alt+Backspace and "voilá"!

So only what I'm missing is about the 3D so loking for any help....

cheers!

---

