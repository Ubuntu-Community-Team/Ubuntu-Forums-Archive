---
title: "Xorg.conf"
date: 2008-12-04
forum: Multimedia Software
---

### Post by mystik10801 on 2008-12-04
I've googled a thousand topics, and none of them are sufficient in helping resolve my issue. Any time I enable the Nvidia advanced graphics drivers, I have no greater than 640X480 resolution, where I should be at 1024X768. I know I have to manually input my desired resolution in the driver because over the course of releasing newer versions of ubuntu, they still can't fix this simple issue, and everytime I figure it out and get my machine like I want it, there's another update that ruins my entire progress. I just need the command to actually edit my xorg.conf file. sudo [something-or-other]

---

### Post by eternalnewbee on 2008-12-05
```
gksudo gedit /etc/X11/xorg.conf
```
is I think the command you're looking for. Found it in this thread:
[http://ubuntuforums.org/showthread.php?t=364201](http://ubuntuforums.org/showthread.php?t=364201)

---

### Post by mystik10801 on 2008-12-05
Yes, gksudo gedit is the command... maybe if I post my Xorg.conf file, someone will see the issue and be able to help (sorry for the needless rant about Linux being a hassle - yesterday wasn't my best day)...


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Nvidia Geforce 6200"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024@60" "1024x768@60" "800x600@60" "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

I found the "Screen" and "Display" sections from another post, but with no luck. The code still doesn't effect in a higher resolution than 640x480. I customized the Identifier under section "Device" myself from another post by someone who was using the same video card I am. 

My thanks for the assistance... Linux IS a much more stable OS than Windoze - not to mention that it really builds your patience... if it doesn't break you first =P

Also, an additional thanks for  your help on the command gksudo gedit eternalnewbee... it's nice that people make the effort, even though half my post was my negative ranting... sorry for that.

---

### Post by overdrank on 2008-12-05
Hi and what version of Ubuntu are you using? If Hardy 8.04 you can try the command ```
gksu displayconfig-gtk
``` and adjust there.
Have you tried using the nvidia settings to adjust ```
gksu nvidia-settings
```
If all else fails try booting into recovery mode and use the xfix option to correct the graphics issues.
Moved to Multimedia & Video  :)

---

### Post by eternalnewbee on 2008-12-05
> (sorry for the needless rant about Linux being a hassle - yesterday wasn't my best day)
That was no rant. Just showing frustration, about the fact you couldn't find the solution anywhere.
Meanwhile I found something that might be interesting for you:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

---

### Post by mystik10801 on 2008-12-05
> **eternalnewbee said:**
> Meanwhile I found something that might be interesting for you:
[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

That actually opens an entire new can of worms, which I've already partly looked into, such as issues with installing those drivers on Ubuntu 8.04 specifically. A) There's the issue of exiting X Server. I found a site that said how exactly, but have lost it since. B) There's a whole other set of issues with making several different checks to ensure there's no driver conflicts that went beyond a simple check and was quite involved according to another lost source. Obviously these drivers on the nvidia site you mentioned eternalnewbee would most likely be preferred, but it would be nice to deal with the issue of installing these from within the Ubuntu forum itself. I downloaded the latest nvidia drivers for my video card, being NVIDIA-Linux-x86-177.82-pkg1.run

Also, concerning your post overdrank, gksu displayconfig-gtk and gksu nvidia-settings, the prior enabled me to raise my screen resolution to 1280x1024 after some time. It was weird, because the first time I ran the function, it didn't go higher than 800x600. After about an hour, I ran the function again and got it up to the 1280x1024@85... I'm not sure about the 85 part - I hope I don't burn up my monitor, but I like the higher resolution. Now, however, I can't seem to get the desktop visual effects enabled for some reason. Your help is appreciated. I'm starting a notebook for functions and codes, and thanks to everyone for their help. I'm going to move toward an entire home network of Linux machines. I've been leaning that way, and my issues truly being few, I can at least set up my other three machines as dual boot OS'. 

Thanks,
Mystik

---

### Post by Yellow Pasque on 2008-12-05
You can try adding modes manually with cvt. For example:
```
cvt -v 1024 768 60.0Hz
```
returns something like:
```
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
```
Copy/paste the Modeline into the Monitor section of your xorg.conf

[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)

---

