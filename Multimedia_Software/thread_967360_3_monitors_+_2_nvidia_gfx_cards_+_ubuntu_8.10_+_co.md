---
title: "3 monitors + 2 nvidia gfx cards + ubuntu 8.10 + compiz = possible?"
date: 2008-11-02
forum: Multimedia Software
---

### Post by iSTRONG on 2008-11-02
I have a 8800 GT and a 8400 GS

I have 3 monitors of same resolution (2 on the dual-head 8800 and 1 on the 8400 GS)

Is there anyway i can have all of the monitors working as "one big screen" ie. ability to drag windows between screens and also have hardware acceleration.

It used to be possible with Hardy through xserver-xgl but xserver-xgl is not included in Intrepid.

So basically i want to do what this guy did ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=884161](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=884161)) but with 3 screens only and on 8.10 instead of 8.04

Possible?

---

### Post by iSTRONG on 2008-11-02
bumpidibump

---

### Post by Red Dot on 2008-11-10
I'm having similar issues with 8.10. Xinerama worked great on 8.04 across 3 monitors using 2 NVIDIA cards (1 PCIe and 1 PCI). However, now the PCI card crashes X every time I enable the 3rd screen.  The below setup worked fine on 8.04 with the right screen enabled.

Anyone else running into this problem?

```
#--------------------------------------------------
# Server Layout
#--------------------------------------------------
Section "ServerLayout"
    Identifier     "Three Monitor Layout"
    Screen         "Screen Middle" 0 0
    Screen         "Screen Left" LeftOf "Screen Middle"
    #Screen         "Screen Right" RightOf "Screen Middle"
    InputDevice    "Enermax Aurora"
    InputDevice    "Microsoft Laser Mouse 6000"
EndSection

#--------------------------------------------------
# Module
#--------------------------------------------------
Section "Module"
    Load	   "GLcore"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "v4l"
    Load           "vbe"
    Load           "glx"
EndSection

#--------------------------------------------------
# Server Flags
#--------------------------------------------------
Section "ServerFlags"
    Option         "Xinerama" "true"
EndSection

#--------------------------------------------------
# Input Devices
#--------------------------------------------------
Section "InputDevice"
    Identifier     "Enermax Aurora"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc101"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Microsoft Laser Mouse 6000"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Buttons" "9"
    Option         "ZAxisMapping" "4 5"
    Option         "DialRelativeAxisButtons" "6 7"
EndSection

#--------------------------------------------------
# Monitors
#--------------------------------------------------
Section "Monitor"
    Identifier     "Viewsonic VX910"
    VendorName     "Viewsonic"
    ModelName      "VX910"
    Option         "DPMS"
EndSection

#--------------------------------------------------
# Devices
#--------------------------------------------------
Section "Device"
    Identifier     "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BusID          "PCI:5:0:0"
EndSection

#--------------------------------------------------
# Screens
#--------------------------------------------------
Section "Screen"
    Identifier     "Screen Middle"
    Device         "0 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Viewsonic VX910"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen Left"
    Device         "1 nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Viewsonic VX910"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen Right"
    Device         "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "Viewsonic VX910"
    DefaultDepth    24
    Option         "BusType" "PCI"
    Option         "NoLogo" "True"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
EndSection
```

---

### Post by gummiwalze on 2008-11-11
Yeah, I am having this problem too.  I have a 1920x1200 on 8800GTS512 and (2) 1600x1200 on 7900GTX, and I can't get this to work right anymore.

It's not JUST ubuntu though:  Fedora 10 RC is having the same issue, and in fact my Fedora 9 system started doing it a week or so ago after I updated and it got a new kernel and xorg server.  I had the issue with a couple of other Linuxes as well, when I updated them to the latest.

I think we are stuck until NVidia updates their binary driver to fully support xrandr, at which point we should be able to do anything we want again.  At least, that's the rumor I keep hearing when I ask about this issue.

In the mean time, either roll back to 8.04 somehow, or put up with it ](*,)

---

### Post by Red Dot on 2008-11-19
That's what I figured.  I guess I'll just wait until the drivers are updated.  Too much effort to roll-back.

---

### Post by Red Dot on 2008-12-13
Finally got this working.  All I needed to do was disable glx in the Module section.  Apparently glx has issues with Xinerama enabled.

```
#--------------------------------------------------
# Module
#--------------------------------------------------
Section "Module"
    Load           "extmod"
    Load           "dbe"
    Load           "freetype"
    #Load           "glx"
    Disable        "glx"
EndSection
```

---

### Post by iSTRONG on 2008-12-14
hmmm interesting redot... thanks for coming back here and posting a solution.

Do you know what the X server system falls back on when you disable GLX?

---

### Post by iSTRONG on 2008-12-15
red dot; i tried your solution but it disables desktop effects / compiz.

I don't want to lose hardware acceleration...

---

### Post by iSTRONG on 2008-12-15
After a bit more research I've come to the conclusion that this is just not possible right now.

You could use xserver-xgl with 8.04 ([http://ubuntuforums.org/showthread.php?t=884161&page=3](http://ubuntuforums.org/showthread.php?t=884161&page=3)) but this is not possible in 8.10 anymore because xserver-xgl has been removed from repos.

If you install it from .deb then you have problems with HAL which controls 8.10

So the solution seems to wait for new nvidia drivers or randr 1.3 (or go back to 8.04 and use xserver-xgl)

anyways, that's what i understood from what i've read...

---

### Post by Red Dot on 2008-12-17
Sorry iSTRONG.  My solution was without Compiz enabled.  I should have mentioned that.

> So the solution seems to wait for new nvidia drivers or randr 1.3 (or go back to 8.04 and use xserver-xgl)

I agree, I think we need wait for NVIDIA to update for a fully-functioning solution.

---

