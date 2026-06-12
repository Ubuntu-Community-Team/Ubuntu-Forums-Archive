---
title: "HSync problem with Samsung LCD and NVidia Geforce3"
date: 2008-11-08
forum: Multimedia Software
---

### Post by TristanSt on 2008-11-08
I'm having problems with the horizontal alignment since upgrading to intrepid - essentially the display is about 12mm too far to the left of my screen giving me a black line down the right hand side.

Reading other posts, this seems fixable using xvidtune, however when I run that I'm getting "Unable to query monitor info", presumably because I'm using the nvidia X Server.

The easy way to fix this is to press the "auto" button on the front of the monitor, however when I go into Windows I then have the opposite problem. This wasn't an issue for me under Hardy so I'm sure that it is fixable.

My xorg.conf file is as follows
> <snip>
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"

	#	Option		"UseFBDev"		"true"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection


whereas before the upgrade it was:
> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        #       Option          "UseFBDev"              "true"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
EndSection

For info, my graphics card is a GeForce3 Ti200 and the monitor is a Samsung SyncMater 713BM.

Thanks

---

### Post by r0g on 2009-08-27
bump!

---

### Post by howitee on 2009-10-25
Also same problem - whole X screen is too big for monitor (Samsung HD TV) - by approx 10% - missing top and bottom bars and sides...

---

