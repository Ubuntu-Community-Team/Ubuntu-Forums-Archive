---
title: "limited resolution"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Garmuar on 2008-07-30
I had no problem getting screen res of 1024x768 with xp running on my old hp pavilion using RIVA TNT2 pro video card.  Now with Ubuntu (gusty) on same machine I am limited to 800x600 with any driver I try, default or restricted nvidia legacy drivers.

Why is this?  800x600 is too small for my purposes.  Is there any way to increase the desktop size?

---

### Post by overdrank on 2008-07-30
> **Garmuar said:**
> I had no problem getting screen res of 1024x768 with xp running on my old hp pavilion using RIVA TNT2 pro video card.  Now with Ubuntu (gusty) on same machine I am limited to 800x600 with any driver I try, default or restricted nvidia legacy drivers.

Why is this?  800x600 is too small for my purposes.  Is there any way to increase the desktop size?

Hi and can you post the output of the command ```
cat /etc/X11/xorg.conf
```and pleas use the code tags # in the top of the message box on the reply.

---

### Post by Garmuar on 2008-07-30
here it is.

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
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
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
        Identifier      "A70"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
        Monitor         "A70"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

### Post by overdrank on 2008-07-30
> **Garmuar said:**
> here it is.

```
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
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
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
        Identifier      "A70"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
        Monitor         "A70"
  [COLOR="Red"]      Defaultdepth    24[/COLOR]
        SubSection "Display"
                Modes           "1280x1024"     "1280x960"      "1152x864"     "1024x768"       "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

Hi and you  may try and change the default depth from 24 to 16. This may help. You can use the command ```
gksu gedit /etc/X11/xorg.conf
```
Also are you able to choose anything other than 800x600 in screens and resolutions?

---

### Post by Garmuar on 2008-07-30
the only available options were 800x600 and 640x480.

Changing to 16bit color didn't fix the problem.

I noticed in the subsection "display" category in the report that there were other "modes" 1024x768 listed.  Should I be able to use those display sizes??

---

### Post by overdrank on 2008-07-30
> **Garmuar said:**
> the only available options were 800x600 and 640x480.

Changing to 16bit color didn't fix the problem.

I noticed in the subsection "display" category in the report that there were other "modes" 1024x768 listed.  Should I be able to use those display sizes??

Yes, you can try the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by Garmuar on 2008-07-31
OK.  This was a new install so I re-installed.
using the default video drivers I could get up to 1024x768 res.
switching to the nvidia legacy drivers I could only get up to 800x600.

when trying to manually switch desktop size using above command, i could only select up to 800.  I did notice in the drivers tab of that utility, it said "nvidia" in the dialog box.

I then chose select driver by manually, and chose the "nvidia legacy card" off the provided list.  Then it identified my vid card and displayed Riva TNT2, instead of just "nvidia". 

After this everything worked and I have 1024x768 desktop.  
So, the restricted driver utility DID NOT identify my card properly or did not install the driver properly when I ran the utility the first time.

just a heads up.

---

