---
title: "GeForce 7900GS nightmare"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by xer0kill on 2007-11-19
**Sorry for the length of this post. The gist of my problem is down a bit and bolded.**

I'm using Gutsy 64bit version. I had nightmares with this card (7900GS) in the 32bit version as well.I installed the driver with Envy and it worked fine for 2 days, then after I ran the Quake Wars demo (which didn't set my screen resolution properly) the next time I booted up some of my driver files were missing and it couldn't load. I reinstalled the driver with Envy and it worked fine again for another day or two (Quake Wars disappeared from my HDD magically too, isn't that strange?). I had even more issues after running the Doom3 game demo, and couldn't get the driver to work at all after that. So I said "screw it" and decided to reinstall Ubuntu altogether.

I can't run Envy now because I have no CD-ROM (I installed it off of a thumbdrive.. wow what a pain that was to figure out) and it wants some files from the Ubuntu CD. So I manually installed the driver, which wasn't too hard. I downloaded it from nvidia.com and this is what I did: 
```
sudo /etc/init.d/gdm stop (then I pressed ctrl+alt+F1 to get a usable terminal)
sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run
sudo /etc/init.d/gdm start (then I hit ctrl+alt+F7 to get X to come up)

```

It worked great after that! Until something happened in my game that got it stuck in a window and I couldn't alt+tab or alt+enter out of it. Not even alt+f2 was working. **So i did ctrl+alt+F1, got a terminal and ctrl+alt+del. Now everytime it boots up, it says "kernel alive" at the bottom of the screen and it loads up a terminal before trying to go into X. It sits there and tries different graphics modes, none of which seem to work, until it hits 800x600. It basically loads into failsafe mode. I have even tried re-installing the driver and it does the same thing.**

Here's my xorg.conf, even though it keeps getting changed to a failsafe version everytime I boot up:

```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "CPD-E540"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "CPD-E540"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "2048x1536" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

If anyone could help me with this I would be eternally grateful. This is driving me absolutely crazy!:confused:

---

### Post by xer0kill on 2007-11-19
Okay, here's an update! I reran the xserver configuration and reset everything. Then I reinstalled the nvidia driver, the same way I mentioned in the first post. It worked fine again, until I rebooted. It's loading me in failsafe mode again. :(

---

### Post by dabl on 2007-11-19
> **xer0kill said:**
> 

I installed the driver with Envy

  You had the right idea there!

> 

 after I ran the Quake Wars demo (which didn't set my screen resolution properly) the next time I booted up some of my driver files were missing and it couldn't load.

 

Too weird -- are you saying a software demo removed installed files?  If so, that was MORE than a demo package!

> 

 I reinstalled the driver with Envy and it worked fine again for another day or two (Quake Wars disappeared from my HDD magically too, isn't that strange?



I don't actually believe in magic -- either it is still there, or it was removed by someone's choice.

> 

I can't run Envy now because I have no CD-ROM (I installed it off of a thumbdrive.. wow what a pain that was to figure out) and it wants some files from the Ubuntu CD. 



OK this doesn't make a ton of sense -- you can post on this forum but you can't download the little tarball file on [[COLOR="SeaGreen"]** this**[/COLOR]](http://albertomilone.com/nvidia_scripts1.html) page?  And you can open Synaptic, go to "Manage Repositories" and "remove" the installation CD from the repositories list.  That will stop the annoying request for the installation CD.

> 

It worked great after that! 



Well, not really!  :lolflag:

OK, here's a little guidance:

[http://kubuntuforums.net/forums/index.php?topic=3086232.0](http://kubuntuforums.net/forums/index.php?topic=3086232.0)

And here's my xorg.conf file which runs my EVGA GF 7900GS perfectly:

```
Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 130.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GS]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GS"
    Option	   "Coolbits"  "1"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "2048x1536" "1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1200 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 832x624 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

To set the default resolution, after you have reinstalled the driver, open a console window and enter ```
sudo nvidia-settings
``` click the "X Server Display Configuration" tab, click "detect display", then set the resolution.  I recommend leaving the refresh on "Auto" but you can set it if you insist.  When you're happy with the settings, click the "Save to X Configuration File" button in the lower right, "x" the "merge" window, and choose OK, and you're done.  :)

---

