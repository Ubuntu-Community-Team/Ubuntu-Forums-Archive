---
title: "NVidia, Matrox TH2GO, 5760x1080 res, Twinview"
date: 2009-10-24
forum: Multimedia Software
---

### Post by bundabrg on 2009-10-24
Hi All,

I've been running a triple head setup using a Matrox TripleHead2Go Digital Edition with three screens who each have a resolution of 1280x1024 bringing my total screen estate to 3840x1024. I have them mounted on an ergotron triple head mount.

This works great, compiz cube looks awesome and when I boot to Windows my triple head gaming is just amazing. I have an NVidia 9600GT and it handles this resolution without any issue (120fps in Call of Duty 4 with a res of 3840x1024)

I set in compiz the resolution of each screen (disable its 'auto-detect'), and in xorg I have a XineramaInfoOveride that specifies 'fake' xinerama info about the monitors so maximizes will only maximize to each screen, and gnome toolbar are limited in the screens.  It works perfectly!

I decided to bring that setup to my work office, and have bought myself a new set of screens, and another TH2GO. The screens have a resolution of 1920x1080. This brings the full screen estate to 5760x1080.

Now those in the know will point out that the TripleHead2Go can't handle that resolution. However what I am doing is this: -
[LIST]
[*]I've hooked up two screens to two of the TH2Go ports and the TH2GO is connected to port 2 on my dual dvi 9600GT.
[*]I've hooked the third to the first port of my 9600GT
[*]I've updated the TH2GO to support a resolution of 3840*1080
[*]I've updated compiz to reflect the new 'virtual screen' config
[*]I've updated xorg.conf's XineramaInfoOverride to reflect the new screen resolutions.
[*]Setup NVidia Twinview so it spans across the 1920x1080 display and the 3840x1080 display.
[/LIST]

It almost works. 
[LIST]
[*]I can log in, and I get a full desktop of 5760x1080. Good.
[*]I can spin the cube 100% fine and all compiz effects work perfectly and with breathtaking speed. Good.
[*]The gnome toolbars are limited to each screen. That is, each screen has its own toolbar. Good.
[*]If I maximize a window, it maximizes across all three screens. Bad!
[/LIST]

Now my understanding is that maximizing a window will make use of any xinerama info (or fake xinerama info in this case). I would think that the fact gnome-toolbars are correct means xinerama info is fine, however I found this small program online called 'xinerama-info' to query xinerama info, and it returns the following: -

```

Xinerama is enabled on :0.0 (3 screen(s) available)
Xinerama screen 0: 1920x1080+0+0
Xinerama screen 1: 1920x1080+1920+0
Xinerama screen 2: 1920x1080+3840+0

```

So Xinerama info is correct.

My xorg.conf is: -
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    #Option "TwinViewXineramaInfoOverride" "1280x1024+0+0, 1280x1024+1280+1, 1280x1024+2560+0"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    Option         "TwinViewXineramaInfoOverride" "1920x1080+0+0, 1920x1080+1920+0, 1920x1080+3840+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    Option	"DynamicTwinView" "false"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
(I've disabled DynamicTwinView in case it was the cause, but it makes no difference if its enabled or disabled).


My Compiz 'Detect Outputs' is unchecked, and 'Outputs' is set to: -
```

1920x1080+0+0
1920*1080+1920+0
1920*1080+3840+0

```

Is there anything you can think of that I've missed?

Thanks,
Brendan

--Edit--

I ended up disabling compiz, which fixes the problem, then re-enabling it with default settings, which still works, and then re-setting everything back up... which still works. Go figure.

Problem solved.

Brendan

---

### Post by David Tomic on 2009-12-10
Hi Bundabrg ...

Funnily enough, I'm actually trying create *exactly* the same setup you've just created, but I've run into a problem trying to set the Matrox resolution. You wrote:

> # I've updated the TH2GO to support a resolution of 3840*1080

... but I can't work out how to do that myself?!?

Without modifying anything, the Matrox defaults to a resolution of 3840*1200, but the display looks pretty ordinary because the monitors aren't running at their native resolution.

I've tried fiddling around with xorg.conf a little bit to try and force a different resolution, but I haven't really had any luck yet.

Any suggestions?

Thanks!

--David

---

### Post by bundabrg on 2009-12-10
Hi David,

I hope you have access to a Windows machine. You'll need to plug the TH2GO into it, install the Matrox TH2GO software (download the latest from the web). The software allows you to reset what modes the TH2GO supports.

I removed all the modes I'm unlikely to use, and added all the ones that I would need, including 3840x1080


Good Luck,
 - Brendan

---

### Post by David Tomic on 2009-12-11
Ahhh ... I figured that it probably involved something like that.

Luckily there's still a couple of Windows machines in the house, so I'll go and try my luck with one of them.

Thanks for the help ...

--David

---

### Post by David Tomic on 2009-12-11
Well ... SUCCESS!

I've even managed to get the Xinerama working properly as well! ;)

Thanks a lot for your help Bundabrg ... I'm sure that you saved me from a lot of un-necessary frustration!

Cheers!

--David

---

