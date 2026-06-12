---
title: "LCD TV as a second monitor"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by vassalle on 2007-10-15
Greetings fellow ubuntuians,

**Current SETUP**
I've recently bought a Toshiba 42 inch LCD TV [(SPECS)]("http://www.toshiba.com.my/servlet/svtUProductPage?func=spec&proID=2538671500") and hooked it up to my Gutsy.

Currently, I'm connecting the monitor to my PC using **VGA** cable, connected to my **Nvidia 8800GTS** graphics card. I'm using  **Nvidia binary driver** ( the latest **100.x.19 installed via envy**). I have inserted some lines into my xorg.conf as per the ubuntuguide[ (LINK)]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn")
```
##This turns on NVidia’s TwinView
Option "TwinView"
##Here I’m setting the resolution to the individual monitors.
Option "MetaModes" "1024x768 1024x768"
```

I've also changed the Twinview settings via the Nvidia-settings GUI - changing the setup to **CLONE** (the default was a horizontal extension).

My first monitor is an Acer 22 inch with a native resolution of 1680x1050.

**QUALMS and QUESTIONS ON HOW TO IMPROVE**
Due to the difference in aspect ratio, the Acer is on a 1680 while my toshiba is at 1024, the image that comes out from my toshiba is somewhat 'cropped'. Probably this is called overscan (not too sure about the terminology).* If I were to play a 350mb avi video file using mplayer on fullscreen, i can only see parts of it on my toshiba while shown in full on my Acer.*

***Q1. How do I set up my system to enable me to enjoy fullscreen videos on my Toshiba? ***

The* quality of the output from my Toshiba is not that great*, probably due to the fact that I connected it using VGA. 

***Q2. Would I see any significant improvement if i were to connect it via a HDMI-DVI cable? (HDMI to monitor, DVI to my 8800). Do I need to change any of my Nvidia or xorg settings if I were to change it? What resolutions can I get if i were to use this method?***

Hopefully someone clear up some of my concerns and provide viable solutions that could improve my current setup. Thanks in advance!

---

### Post by W. Irving on 2007-10-21
You will see a tiny improvement with a DVI/HDMI cable. VGA, being analogue, can very well pick up interference - and the quality is also cable dependant, which is not the case with HDMI. I'm not entirely sure about the resolutions available, but I believe a TV expects VGA/SVGA/XGA/WXGA resolutions on the VGA interface, but it's a different matter with HDMI - which seems to use HDTV resolutions (576p/720p/1080p and so on) instead.
xorg.conf should need reconfigurating if you swap interface.

I'm dealing with a severe case of overscan myself at the moment, so no ideas there. :)

---

