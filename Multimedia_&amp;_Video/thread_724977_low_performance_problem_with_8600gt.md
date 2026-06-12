---
title: "low performance problem with 8600gt"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by Cineq on 2008-03-15
Hi All

I have serious problem with my graphic card GF 8600 gt. I`m running Kubuntu 7.10 on compal IFL 90. The problem is that i have very low fps level... I tried everything. At first i had installed nvidia drivers by restricted manager, after that i tried with envy. CPU scaling is enabled and switched on maximum level. I`m reading forum from few days but there is nothing to solve my problem. I`m noob in linuks so please give some advices to find the way i could solve my problem. 

i also tried compiz fusion and beryl-in both of them was the same low fps level

and sorry for my english I`m writting friom Poland;)

---

### Post by askreet on 2008-03-17
First thing you need to do is confirm that your video hardware is actually being hardware accelerated after installing the restricted drivers.

At a commandline:

```
glxinfo|grep Direct
```

You should see:
```
Direct Rendering: Yes
```

If you do not, please paste the output that you do see here.  Also, include the output of:
```
lsmod|grep nv
```

and
```
cat /etc/X11/xorg.conf
```

---

### Post by Cineq on 2008-03-20
when I type
```

glxinfo|grep Direct

```

then nothing is shown

```
nvidia               7825664  36 
i2c_core               26112  1 nvidia
agpgart                35016  2 nvidia,intel_agp
```


```
Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier      "Default Layout"
  screen "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pl"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Horizsync       28.0    -       64.0
        Vertrefresh     43.0    -       60.0
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8600M GT]"
        Driver          "nvidia"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8600M GT]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "DisableGLXRootClipping"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
                Modes           "1280x1280"
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection




```

---

### Post by jacob01 on 2008-03-20
is it the 8600 used in laptops or is it the regular 8600 gpu? What drivers are you using, it looks like you are using the proprietary driver from nvidia because you have "nvidia" in your xorg. If you are using the ones from the repository then i believe it should be "nv" for the driver.

I noticed slow speeds after installing the xgl package for running compiz, i think it messed up my xorg file so i removed the xgl package and reinstalled driver now things work good. Try to remove the xserver-xgl package if it is installed then restart your x.

---

