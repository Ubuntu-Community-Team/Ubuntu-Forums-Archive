---
title: "Nvidia Twinview weird metamode behavior"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by shanek on 2007-08-06
I'm running Kubuntu 7.04 on an AMD64 system with an Nvidia GeForce 6200 video card.

My trouble is that the metamodes in a Twinview setup don't seem to behave the way I thought they should. Maybe I'm missing something. I have a  metamode for the normal twinview setup with two 1280x1024 screens right next to each other, and a metamode for fullscreen games using just the one screen. If I have both metamodes in my xorg.conf, I always end up with only the 1 screen working. If I take out the fullscreen metamode (which is listed second) I get what I was looking for. Two screens side by side, and windows know to only maximize to one screen. Of course, if I try to play UT2K4, it tries to straddle both screens. How do I get both? I had this working ages ago on a Gentoo system, so I know that this card is capable of it.

Here's an excerpt from my xorg.conf:

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       25.0 - 70
    VertRefresh     50.0 - 120
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia 6200"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
    Option "TwinView" "True"
#    Option "HorizSync" "31-96"
#    Option "VertRefresh" "50-100"
#    Option "SecondMonitorHorizSync" "31-96"
#    Option "SecondMonitorVertRefresh" "50-100"
#    Option "UseEdidFreqs"
#    Option "UseDisplayDevice" "CRT, CRT"
#    Option "DynamicTwinView" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1280x1024,NULL; 1024x768,1024x768; 1024x768,NULL"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia 6200"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "2560x1024"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "2560x1024"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "2560x1024"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "2560x1024"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "2560x1024"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "2560x1024"
    EndSubSection
EndSection

---

### Post by dougfractal on 2007-08-06
I don't know if this is any use.
you would have to sudo /etc/init.d/gdm stop
and then startx -- -layout single

but you would have multiple layouts in 1 xorg.conf file

[http://gentoo-wiki.com/Twinview_Example](http://gentoo-wiki.com/Twinview_Example)
 > X Setup

This shows the X config file /etc/X11/xorg.conf. All three ServerLayouts can be used without changing the file. 

Starting X

The layout in use is selected in the Section ServerFlags with the option

Option "DefaultServerLayout" "twinview"

When using startx command, you can use parameters to start the right ServerLayout:

startx -- -layout twinview
startx -- -layout xinerama
startx -- -layout single


---

### Post by shanek on 2007-08-06
Yeah, that's not quite what I'm looking for.

In my old Gentoo setup, I just selected UT2004 or BZFlag (or whatever) from the regular K menu, and it automatically switched over to single screen mode. When I was done playing, it automatically switched back to two screens as I exited the game.

---

### Post by dougfractal on 2007-08-06
I think its here

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#Nvidia](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Nvidia)
> 
Most 3D apps are not prepared for a double-width resolution (including, for example, UT2004) and will annoyingly appear in the middle of the virtual screen, across the split, unless you specify a MetaMode at the correct resolution for only one monitor (see Device section given below).

For full screen games, you will probably want at least one single-monitor MetaMode (eg: 1280x1024; ) that the game can use.
Section "Device"
Option     "MetaModes"  "1280x1024,1280x1024; 1280x1024; 1024x768,1024x768; 1024x768; 800x600,800x600; 800x600"

adjust this
> #Section "Device"
# Option "TwinViewOrientation" "CRT-0 RightOf DFP-0"
#    Option "HorizSync"   "DFP-0: 30-81; CRT-0: 30-98"
#    Option "VertRefresh" "DFP-0: 56-75; CRT-0: 50-120"

or
# Option "HorizSync" "31-96"
# Option "VertRefresh" "50-100"
# Option "SecondMonitorHorizSync" "31-96"
# Option "SecondMonitorVertRefresh" "50-100"


Section "Screen"
    Identifier	"ScreenTwin"
    Device      "NvidiaTwin"
    Monitor	"TwinMoni"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600"
    EndSubsection
EndSection

---

### Post by shanek on 2007-08-09
Ok, got it fixed - finally.
Here's what I ended up with in my xorg.conf file:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 80.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
#    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Option	"MetaModes" "1280x1024,1280x1024; 1280x1024; 1024x768,1024x768; 1024x768; 800x600,800x600; 800x600;" 
   SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

I think that part of my trouble was the Sylvania F70 monitor that I'm using as the second monitor. I had to tweak the HorizSync and VertRefresh values until it was usable by the second screen.

I've also noticed a downgrade in performance when playing fullscreen games. Maybe I'll experiment with SecondMonitorHorizSync etc. to get my main screen a bit smoother.

---

### Post by dougfractal on 2007-08-10
another way
[http://ubuntuforums.org/showpost.php?p=3157811&postcount=167](http://ubuntuforums.org/showpost.php?p=3157811&postcount=167)
[http://ubuntuforums.org/showpost.php?p=3139747&postcount=1](http://ubuntuforums.org/showpost.php?p=3139747&postcount=1)
You could tweek these scripts to run a seperate X (twm) and hence seperate conf

This is a hotswap X solution.

---

