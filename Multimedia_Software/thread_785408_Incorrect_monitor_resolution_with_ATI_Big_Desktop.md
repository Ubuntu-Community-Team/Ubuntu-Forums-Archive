---
title: "Incorrect monitor resolution with ATI Big Desktop"
date: 2008-05-07
forum: Multimedia Software
---

### Post by iwagner on 2008-05-07
I've been happily running Ubuntu 7.10 with dual monitors since it came out, however I can't get dual monitors to work properly under 8.04.

In Ubuntu 7.10 I set up Big Desktop mode on my ATI Radeon X1300 Pro video card.  I have identical monitors that support a maximum resolution of 1280x1024.  Here is my xorg.conf file that worked for me under Ubuntu 7.10:

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "DELL E197FP"
        HorizSync    31.0 - 80.0
        VertRefresh  56.0 - 75.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        Option      "ForceMonitors" "crt1,crt2"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "DELL E197FP"
        DefaultDepth     24
        SubSection "Display"
                Modes    "2560x1024" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "1"
EndSection

```

Yesterday, I installed Ubuntu 8.04 from scratch onto my machine.  My old xorg.conf file won't work for me though.  What happens is that one of my monitors comes up in 1280x1024 mode, but the other comes up in 1024x768 mode.

So, I tried following different guides, including [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).  I did manage to get a configuration that sort of works.  My current configuration is this:

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "DesktopSetup" "horizontal"
        Option      "Capabilities" "0x00000800"
        Option      "PairModes" "1280x1024+1280x1024"
        Option      "EnableMonitor" "crt1,crt2"
        Option      "ForceMonitors" "crt1,crt2"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
EndSection

```

This works in the sense that I have my Big Desktop, but the monitor resolution is wrong.  Both monitors come up with a 1024x768 resolution.  I can't seem to get the resolution to work properly.

Can anyone help?  How do I get both monitors to have 1280x1024 resolution in Ubuntu 8.04?  I'd rather not go back to 7.10, but I will if I need to.

Thanks.

---

### Post by pro003 on 2008-05-07
did you try:

```
aticonfig --initial=dual-head
```

```
aticonfig --force-monitor=crt1,crt2
```

---

### Post by iwagner on 2008-05-07
> **pro003 said:**
> did you try:

```
aticonfig --initial=dual-head
```

```
aticonfig --force-monitor=crt1,crt2
```


Yes, I did try those commands with no success.  Thanks.

---

### Post by iwagner on 2008-05-08
I solved it.  My config wasn't the problem it is the ATI driver included with Ubuntu 8.04.  I went to ATI's web site and downloaded the latest Linux driver and installed it according to the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide).  The latest driver works fine for me and now I am a happy man.

---

### Post by pro003 on 2008-05-08
glad you made it... i'm still using ubuntu driver, it's fine but maybe i should try the ati's original driver...i never used it with 8.04...

---

