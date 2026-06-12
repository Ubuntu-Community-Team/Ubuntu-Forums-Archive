---
title: "Switching from ati to fglrx creates a mysterious line"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by jmags on 2006-12-03
I'm running 6.10 on an IBM Thinkpad T43. After I switched from the ati to the flgrx driver, a horizontal line appears under my mouse pointer. Any ideas what this might be.

In case anyone can get anything useful from it:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by David Mulligan on 2006-12-09
I just had the same thing happen to me.  Does anyone have a solution to this?  In my case I am using a Dell Latitude D600.

Thanks,
David

---

### Post by andlinux on 2006-12-24
I've got the same problem after upgrading to edgy, I had that in the past too but I can't remember how I fixed it... ](*,)

---

### Post by andlinux on 2006-12-26
The line is away, I'm not using any fglrx based driver, just the ati driver.

---

### Post by mayhemt on 2006-12-26
As far I know/I can recall, you are missing the following stuff mate... i guess extmod is the one which handles the line under cursor...

```


Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection


```

---

### Post by andlinux on 2006-12-27
> **mayhemt said:**
> As far I know/I can recall, you are missing the following stuff mate... i guess extmod is the one which handles the line under cursor...

```


Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection


```
I had that in my xorg.conf when I used the fglrx drivers.
I found on a website that you have to add a # in front of "load composite" and that didn't worked.

Found this website too but that didn't worked for me.
[http://www.thinkwiki.org/wiki/Problems_with_fglrx#Line_Appears_Below_Mouse_Cursor](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Line_Appears_Below_Mouse_Cursor)

---

### Post by mayhemt on 2006-12-27
try the extra options

```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NJ [Radeon 9800 XT]"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
	Option	    "mtrr" "off"
	Option	    "ScreenOverlap" "0"
	Option	    "GammaCorrectionI" "0x06419064"
	Option	    "GammaCorrectionII" "0x06419064"
	Option	    "Capabilities" "0x00000000"
	Option	    "CapabilitiesEx" "0x00000000"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Centermode" "off"
	Option	    "PseudoColorVisuals" "off"
	Option	    "Stereo" "off"
	Option	    "StereoSyncEnable" "1"
	Option	    "FSAAEnable" "on"
	Option	    "FSAAScale" "4"
	Option	    "FSAADisableGamma" "no"
	Option	    "FSAACustomizeMSPos" "no"
	Option	    "FSAAMSPosX0" "0.000000"
	Option	    "FSAAMSPosY0" "0.000000"
	Option	    "FSAAMSPosX1" "0.000000"
	Option	    "FSAAMSPosY1" "0.000000"
	Option	    "FSAAMSPosX2" "0.000000"
	Option	    "FSAAMSPosY2" "0.000000"
	Option	    "FSAAMSPosX3" "0.000000"
	Option	    "FSAAMSPosY3" "0.000000"
	Option	    "FSAAMSPosX4" "0.000000"
	Option	    "FSAAMSPosY4" "0.000000"
	Option	    "FSAAMSPosX5" "0.000000"
	Option	    "FSAAMSPosY5" "0.000000"
	Option	    "UseFastTLS" "on"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "ForceGenericCPU" "no"
	Option	    "KernelModuleParm" "locked-userpages=0"
	Option	    "AGPFastWrite" "True"
	Option	    "EnablePageFlip" "True"
	Option	    "DesktopSetup" "single"
	BusID       "PCI:1:0:0"
EndSection



```

---

### Post by andlinux on 2006-12-28
> **mayhemt said:**
> try the extra options

```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NJ [Radeon 9800 XT]"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
	Option	    "mtrr" "off"
	Option	    "ScreenOverlap" "0"
	Option	    "GammaCorrectionI" "0x06419064"
	Option	    "GammaCorrectionII" "0x06419064"
	Option	    "Capabilities" "0x00000000"
	Option	    "CapabilitiesEx" "0x00000000"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Centermode" "off"
	Option	    "PseudoColorVisuals" "off"
	Option	    "Stereo" "off"
	Option	    "StereoSyncEnable" "1"
	Option	    "FSAAEnable" "on"
	Option	    "FSAAScale" "4"
	Option	    "FSAADisableGamma" "no"
	Option	    "FSAACustomizeMSPos" "no"
	Option	    "FSAAMSPosX0" "0.000000"
	Option	    "FSAAMSPosY0" "0.000000"
	Option	    "FSAAMSPosX1" "0.000000"
	Option	    "FSAAMSPosY1" "0.000000"
	Option	    "FSAAMSPosX2" "0.000000"
	Option	    "FSAAMSPosY2" "0.000000"
	Option	    "FSAAMSPosX3" "0.000000"
	Option	    "FSAAMSPosY3" "0.000000"
	Option	    "FSAAMSPosX4" "0.000000"
	Option	    "FSAAMSPosY4" "0.000000"
	Option	    "FSAAMSPosX5" "0.000000"
	Option	    "FSAAMSPosY5" "0.000000"
	Option	    "UseFastTLS" "on"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "ForceGenericCPU" "no"
	Option	    "KernelModuleParm" "locked-userpages=0"
	Option	    "AGPFastWrite" "True"
	Option	    "EnablePageFlip" "True"
	Option	    "DesktopSetup" "single"
	BusID       "PCI:1:0:0"
EndSection



```

I tried that and it didn't helped, I think it's the drivers.

---

### Post by andlinux on 2007-02-09
I installed Envy and that will download/install the drivers (nvidia or ati) for you. The mysterious line is gone now.

You can find it here: [http://albertomilone.com/index.html](http://albertomilone.com/index.html)

---

