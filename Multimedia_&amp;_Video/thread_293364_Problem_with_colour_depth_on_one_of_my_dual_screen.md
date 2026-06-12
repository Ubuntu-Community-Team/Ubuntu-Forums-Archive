---
title: "Problem with colour depth on one of my dual screens after upgrading to edgy"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by heinkel_111 on 2006-11-05
I am a Kubuntu user, and I posted a similar thread on the Kubuntu forums a few days ago, but I am not getting very much advice. :( Therefore I am posting more or less the same question here:

I have noticed that I get a colour distortion on one of my screens after I upgraded to Edgy. I don't know if it is related to the upgrade at all, but it did not use to be a problem earlier.

**The Symptoms:**
I use a greyscale image for my wallpaper (i have as much as possible in greyscales atm). After the upgrade, I noted that the darker grey shades were being rendered as "petrol stain" greenish-pinkish-blues instead of a smooth transition from dark grey to even darker grey to almost black. 

Below is a screenshot onto which I have indicated where the colours start "folding" into petrol stain instead of darkening as they should do.
[url=http://home.online.no/~thcsp/desktop1_with_problems.png][img]http://home.online.no/~thcsp/desktop1_with_problems_small.png[/img]
[/url]
*click on image for larger version*

I expect that on your screen, it will look quite normal dark grey to black where I get the problem.

**An important observation**
Just  as I was the description for this topic, I noticed that as I moved the GIMP window where I have the screenshot for resizing, the "petrol stain" was removed on the other screen. Moving the window across the desktop, to the first screen again, the petrol stains reappered. 

**What I *think* might be the problem.**
It appears that I don't get a full colour depth resolution at my left screen. I don't know why, but I guess xorg.conf can at least be used to solve the problem. It appears that something that went right by default earlier, now goes wrong....

I have 2 Samsung synCmaster 204B monitors, and a GeForce 7900 Nvidia graphics card. I use digital video connection to the monitors from the graphicscard. 
 
This is my current xorg.conf. I think that my left monitor is currently not getting the 24 bit default resolution:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "record"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "no"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:7:0:0"
        Option "NoLogo" "1"
#       Option "RenderAccel" "0"
#       Option "CursorShadow" "1"
#       Option "Coolbits" "1"
        Option "ConnectedMonitor" "dfp, dfp"
        Option "NoPowerConnectorCheck"
        Option "TwinView" "1"
        Option "Metamodes" "1600x1200,1600x1200; 1600x1200,NULL; NULL,1600x1200"
#       Option "SecondMonitorHorizSync" "31-82"
#       Option "SecondMonitorVertRefresh" "56-76"
        Option  "TwinViewOrientation" "RightOf"
        Option  "UseEdidFreqs" "True"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NVIDIA Default Card"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Viewport 0 0
                Depth           24
                Modes           "1600x1200"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "TwinView Configuration"
        Screen 0        "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama" "Off"
EndSection

Section "DRI"
        Mode    0666

```

It may be caused by a driver bug, as it seems I am no longer able to autoadjust my screen settings. I *think* used to be able to do this, but I am not completely sure because I dualboot the machine and such operations may have been performed while playing games in WinXP.  

It is not a fatal driver error, because everything works on my right-hand monitor. I use a dualscreen set-up with two identical screens.

My guess is  some communication between xorg and my monitor is not working as it should. Because of that xorg does not know what my monitor is capable of and then defaults to 8-bit (wild guess) colour. 

I think that somehow xorg can help fix this, as it should be possible to work around this "broken pipe" kind of problem with hardcoding the correct settings into xorg.conf the correct settings. 

Any clues why I don't get correct color depth?  ???

---

### Post by heinkel_111 on 2006-11-05
Adding information: Problem disappears after Ctrl-Alt-Backspace X server restart. Re-appears at boot.

---

### Post by heinkel_111 on 2006-11-07
edieguez reports a similar colour problem:
[http://ubuntuforums.org/showthread.php?t=289116](http://ubuntuforums.org/showthread.php?t=289116)

Anyone have further suggestions regarding troubleshooting actions?

---

