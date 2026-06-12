---
title: "Multiple monitors and a crappy IBM box that won't behave."
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by ritontor on 2006-07-21
Hi guys, 

I've just installed Ubuntu 6.05 on this crappy little IBM desktop box (a ThinkCenter 8184). It has onboard video (Intel Corporation 82865G Integrated Graphics Device), however, when I initially tried to get it installed and running, I had a Nvidia FX5200 PCI card as the primary display. 

Much to my concern, when attempting to start the X server with that piece of equipment in place, it failed. Flipping through the error log indicated that the X server had at least detected the onboard Intel video. This is where I think the major problem lies. 

As far as I can tell, there is no way to completely disable the onboard video. The BIOS allows you to select the primary display device, but given that the Ubuntu setup still seems to detect it, one has to assume that assigning a lower priority to the onboard video doesn't disable it. So I guess that leaves me with a two part question... 

1. How would I go about getting Ubuntu working nicely with my Nvidia card, without being able to disable the onboard video, and...

2. Is it relatively easy to get dual monitors up and going (there's 2 ports on the Nvidia card, works fine for dual screens) once I have one display working? 

Thanks for your time.

---

### Post by Ziox on 2006-07-22
use lspci-x in terminal to determin the BusID for each card.  Then you have to edit the xorg.conf to enable it...as for dual monitors, i think you have to edit the xorg.conf file as well...if you would like that then, post back...

---

### Post by tseliot on 2006-07-22
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by ritontor on 2006-07-24
Ahh! Thanks guys, using a combination of both those tricks, I worked out how to do it - lspci gave me the pci bus ID so I could build an additional Device section in the xorg config, then used that device in the Screen config.

I'll have a crack at dual monitors now, I'm sure I'll find something in a forum search. If I can't see anything that points me in the right direction, I'll be sure to post. Thanks again!

---

### Post by Ziox on 2006-07-24
check my signature for a howto i wrote for dual monitors...so it works great with ATI cards, but nVidia cards seems to having some trouble with the open source "nv" driver. But give it a try anyway.

---

### Post by ritontor on 2006-07-25
I eventually got it working by using the non-open nvidia driver and twinview, which is worlds ahead in terms of speed over xinerama. Basically, it goes like this: 

1. install the nvidia driver. google around for instructions. 
2. backup your x.org config and then get ready to edit it.
3. Change these 3 sections to look like this. Clearly not everything is going to be the same in your config. Use lspci -X to find the PCI channel your video card is on. 

```
Section "Device"
        Identifier      "Card"
        Driver          "nvidia"
        BusID           "PCI:3:9:0"
        Option "NvAGP" "2"
        Option "NoLogo" "1"
        Option "RenderAccel" "1"
        Option "CursorShadow" "1"
        Option "ConnectedMonitor" "crt, crt"
        Option "NoPowerConnectorCheck"
        Option "TwinView" "1"
        Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
        Option "SecondMonitorHorizSync" "31-82"
        Option "SecondMonitorVertRefresh" "56-76"
EndSection

Section "Screen"
Identifier "Screen"
Device "Card"
Monitor "Monitor"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
EndSubSection
EndSection


Section "ServerLayout"
        Identifier "TwinView Configuration"
        Screen 0 "Screen" 0 0
        Option "Xinerama" "Off"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

```

4. ctrl-tab-backspace and hope you haven't screwed it all up. if you do, log in, copy the backup back in to place, and type startx.

---

