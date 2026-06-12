---
title: "Dual Screen Problem"
date: 2008-07-30
forum: Mythbuntu
---

### Post by kryptonite2k on 2008-07-30
I am trying to use two screens( a TV and a Monitor) on one nvidia graphics card. I have tried using TwinView and setting it up as 2 screens. The only configuration that I could get something to work is the 2 screen configuration, but it only outputs on one screen. It will display on which ever screen is configured first in the xorg.conf. If I switch which display is "Screen0" then it displays on that screen.
Here is the contents of my xorg.conf.

```

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
        BusID   "PCI:01:00:0"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        BusID   "PCI:01:00:0"
EndSection

Section "Monitor"
        Identifier      "Monitor" #CRT
        HorizSync       30-70
        VertRefresh     50-140
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option  "ConnectedMonitor" "CRT"
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "NTSC-M"
        Option  "ConnectedMonitor" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen 0        "Screen0"
        Screen 1        "Screen1" rightof "Screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```  

My video card is the Jaton PX8400GS-LX.
What should I do to get both screens working?

---

### Post by tuxxy on 2008-07-30
Did you install nvidia-settings

---

### Post by kryptonite2k on 2008-07-30
I have not done that. Could you tell me how?

---

### Post by 16777216 on 2008-07-30
Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option  "ConnectedMonitor" "CRT"
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "NTSC-M"
        Option  "ConnectedMonitor" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection

You have no meta-modes that tell twinview the arrangement of the screens.
In most cases you have nvidia-settings allready installed type nvidia-settings into a terminal to see.

---

### Post by kryptonite2k on 2008-07-30
ok, I typed nvidia-settings in and I do have it installed. 
I didn't think I needed to use the "TwinView" option since I was setting it up a 2 X screens. I have tried using the twinview method but it restart into low graphics mode.

---

### Post by 16777216 on 2008-07-30
Adding 
```
Option  "metamodes"  "CRT-0: 1024x768 +0+0, TV: 640x480 +1024+0"
```
to the "Screen" section should work.

---

### Post by kryptonite2k on 2008-07-30
Should that be added to the "Device" section as I've seen in other xorg.conf's or does it matter where it's placed?

---

### Post by 16777216 on 2008-07-30
> **kryptonite2k said:**
> ok, I typed nvidia-settings in and I do have it installed. 
I didn't think I needed to use the "TwinView" option since I was setting it up a 2 X screens. I have tried using the twinview method but it restart into low graphics mode.


You need to setup your screen layout.
Type sudo nvidia-settings into a terminal and enter your password when asked.
When it opens go to the "X Server Display Configuration" option and set the result ion and position of both screens then click the "X Screen" tab then the "Advanced..." button.
Now, click the "Add" button. This will add the metamode to your list of well,.. metamodes. :)

Next click the "Save to X Configuration File" button and choose to merge the files and click ok. Log-out push ctrl+alt+backspace to reset the X server and log back in.

This *should* set everything straight.

---

### Post by 16777216 on 2008-07-30
> **kryptonite2k said:**
> Should that be added to the "Device" section as I've seen in other xorg.conf's or does it matter where it's placed?

I am not sure putting it in the "Device" section would work but it probably doesn't matter.

Here is my xorg.conf if anyone wants to mod and use it for themselves.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

Section "Screen"
    Identifier     "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
    Option        "TwinView"    "1"
    Option        "TwinViewXineramaInfoOrder"    "CRT-0"
    Option        "metamodes"    "CRT-0: 1152x864 +0+0, CRT-1: 1152x864 +1152+0; CRT-0: 1600x1200 +0+0, CRT-1: NULL; CRT-0: 1152x864 +0+0, CRT-1: NULL; CRT-0: 1024x768 +0+0, CRT-1: NULL; CRT-0: 800x600 +0+0, CRT-1: NULL; CRT-0: 640x480 +0+0, CRT-1: NULL"
    Option        "AddARGBGLXVisuals"    "True"
    SubSection "Display"
        Depth    24
    EndSubSection
    Defaultdepth    24
EndSection

Section "Screen"
    Identifier    "Screen1"
    Device        "Videocard1"
    Monitor        "Monitor1"
    Option        "TwinView"    "0"
    Option        "metamodes"    "TV: 640x480 +0+0"
    Option        "AddARGBGLXVisuals"    "True"
    Defaultdepth    24
EndSection

Section "Device"
    # Removed Option "TwinView" "1"
    # Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
    Identifier    "Videocard0"
    Driver        "nvidia"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 8600 GT"
    Option        "Coolbits"    "1"## This is for over clocking ##
    Option        "TwinViewOrientation"    "RightOf"## This is to tell twinview how your monitors are arranged ##
    Option        "NoLogo"    "1"## This removes the nVidia logo when X loads ##
    Option        "RenderAccel"    "1"## This turns on the 3D ##
    Option        "HWCursor"    "1"## This makes the videocard draw the mouse directly ##
    Option        "AllowGLXWithComposite"    "1"## This is for composite desktops ( Compiz and the like ) ##
    Option        "RandRRotation"    "1"## This is for rotating your screen to match what ever weird set up you have ;) ##
    Option        "AllowDDCCI"    "1"## This is for power management ##
    Option        "AIGLX"    "1"## Again for Compiz and such ##
    Option        "DamageEvents"    "1"
    Option        "UseEvents"    "1"
    Option        "TripleBuffer"    "1"
EndSection

Section "Device"
    Identifier    "Videocard1"
    Driver        "nvidia"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 8600 GT"
    Busid        "PCI:3:0:0"
    Screen    1
EndSection

Section "InputDevice"
    Identifier    "Keyboard0"
    Driver        "kbd"
EndSection

Section "InputDevice"
    Identifier    "Mouse0"
    Driver        "mouse"
    Option        "Protocol"    "auto"
    Option        "Device"    "/dev/psaux"
    Option        "Emulate3Buttons"    "no"
    Option        "ZAxisMapping"    "4 5"
EndSection

Section "ServerLayout"
    Identifier    "Layout0"
  screen 0 "Screen0" 0 0
    Inputdevice    "Keyboard0"    "CoreKeyboard"
    Inputdevice    "Mouse0"    "CorePointer"
EndSection

Section "Module"
    Load        "dbe"
    Load        "extmod"
    Load        "type1"
    Load        "freetype"
    Load        "glx"
    Load        "v4l"
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Vendorname    "Unknown"
    Modelname    "DELL  M991"
    Horizsync    30.0    -    96.0
    Vertrefresh    50.0    -    160.0
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Vendorname    "Unknown"
    Modelname    "TV-0"
    Horizsync    28.0    -    33.0
    Vertrefresh    43.0    -    72.0
EndSection

Section "ServerFlags"
    Option        "Xinerama"    "0"
EndSection

Section "Extensions"
    Option        "DAMAGE"    "Enable"
    Option        "RENDER"    "Enable"
    Option        "Composite"    "Enable"
EndSection

Section "Files"
    Rgbpath        "/usr/X11R6/lib/X11/rgb"
EndSection
```

I no longer have the TV attached and don't use the second video card ( the 6100 ) but they seem to do no harm.

---

### Post by kryptonite2k on 2008-07-30
I added metamodes option to the "screen" section and the same thing happens, I get CRT that displays. I went into the nvidia-settings gui and only one screen shows up, the CRT. I chose the advanced option but I don't get an Add button.

---

### Post by 16777216 on 2008-07-30
Hmmm.. What card do you have?
And I think you have to to have the TV powered on when you turn on the computer or else the nvidia driver will not be able to see the TV but I am not sure.
Mine just worked.
I am not sure where to go from here. :(

---

