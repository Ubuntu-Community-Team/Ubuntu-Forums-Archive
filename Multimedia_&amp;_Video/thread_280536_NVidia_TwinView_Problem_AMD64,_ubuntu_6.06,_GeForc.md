---
title: "NVidia TwinView Problem: AMD64, ubuntu 6.06, GeForce 6800XT"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by kakyoism on 2006-10-19
Hi All,

Newbie to ubuntu and linux in general..:P
My desktop is as title and I've tried the two
most popular How-To's. They both didn't work for me.
The nVidia driver is succesfully installed, and
Below are my xorg.conf after being edited according
to the How-To's: bolded part is my edit.
-----
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NVIDIA Default Card"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"
    Option "UseEdidFreqs" "True"
    Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
    Option "ConnectedMonitor" "DFP, DFP"
    Option "UseDisplayDevice" "DFP"
    Option "NoPowerConnectorCheck"
    Option "SecondMonitorHorizSync" "31-82"
    Option "SecondMonitorVertRefresh" "56-76"
    Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
    Identifier    "DTECH9151"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DTECH9151"
    DefaultDepth    24
    SubSection "Display"
        Viewport 0 0
        Depth        1
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        4
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        8
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        15
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        16
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
    SubSection "Display"
        Viewport 0 0
        Depth        24
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen    0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
    Option "Xinerama" "Off"
    Option "Clone" "Off"
EndSection

Section "DRI"
    Mode    0666
EndSection
-----

And below is my xorg.conf backup
-----
Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x- ttcidfont-conf.d/dirs/TrueType"
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
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "NVIDIA Corporation NVIDIA Default Card"
    Driver        "nv"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "DTECH9151"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DTECH9151"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection
-----

After reboot, the right screen is working properly with the nVidia logo visible.
But the left one is completely dark. The official weblink for the left one is
here:[http://www.lge.com/products/model/detail/l1917s_1_6.jhtml](http://www.lge.com/products/model/detail/l1917s_1_6.jhtml)

I don't know if tuning resolution would help but the max reso I could get from the system preference is 1280x1024 instead of the double size said in the How-To's.

I have tried almost everything on the net by even installed core for k7 but it still wouldn't work. Any idea is appreciated.

Beinan

---

### Post by tseliot on 2006-10-19
Boot in Recovery mode (select it from the GRUB menu almost as soon as you turn on your computer) so as to get to the command line.

Then type
```
nvidia-xconfig --no-composite
```

and then:
```
reboot
```

---

### Post by kakyoism on 2006-10-19
help please~~~

---

### Post by kakyoism on 2006-10-21
please help!!!

---

### Post by tronica on 2006-10-21
heres the best way imho to get dual monitors on a dual head card to work right. and its easy

first install the driver. Comment out "dri" in the Module section. Then in the Device section chande "nv" to "nvidia" and add this to the end of that section

> Option		     "twinview"

Restart X and thats it, it works for me everytime on any distro more specific ubuntu.  Never fails, thats all you need. so in your case i would start over on your xorg.conf.

---

### Post by kakyoism on 2006-10-21
thank u so much!
u r a life-saver man!
works perfectly!
i wish you could write a sticky how-to and replace the existing ones, just 3 lines!

---

### Post by rjolley on 2006-10-28
I cant believe it was that easy, ive been struggling with this for 3 days now, and that was all I needed? Maybe it has something to do with similar vid cards pcie 6800gs here.  Anyway, I assume that getting games to work will be a different story, but this is better than where I was at 10 minutes ago which was twinview working, but one monitor at 1280x1024 the other at 1024x768 if I tried to go higher on the second monitor it would just black out and make my first monitor scrollable at 2560x1024 resolution.  Anyway thanks a lot, other guides should mention to try this first, than do all the wonky stuff they suggest second.
Rex

---

### Post by racepics on 2007-01-17
I cant get it to work properly :(
I've redone it dozens of times.
I used adept to load the nvidia glx driver ( is that the correct one? ) and followed tronica's instructions to the letter.
While the second LCD does come up after the mod the screen res on both drops to about 800x600 instead of the 1440x1050 it should be on a pair of 20" LCDs
Before doing the "option "twinview" thing the no1 screen is showing correct resolution.
As soon as I make the mod, both screens drop to about 800x600 and I cant find away to correct the resolution. :confused:
MSI PCI-E,NX7600GS,256M,Dual DVI and 2x CMV T38D

---

### Post by chipmonk010 on 2007-01-22
> **racepics said:**
> I cant get it to work properly :(
I've redone it dozens of times.
I used adept to load the nvidia glx driver ( is that the correct one? ) and followed tronica's instructions to the letter.
While the second LCD does come up after the mod the screen res on both drops to about 800x600 instead of the 1440x1050 it should be on a pair of 20" LCDs
Before doing the "option "twinview" thing the no1 screen is showing correct resolution.
As soon as I make the mod, both screens drop to about 800x600 and I cant find away to correct the resolution. :confused:
MSI PCI-E,NX7600GS,256M,Dual DVI and 2x CMV T38D

Try removing all the options in your devices section and copy/paste this in:

Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"
Option "UseEdidFreqs" "True"
Option "Metamodes" "1440x1050, 1440x1050"
Option "UseDisplayDevice" "DFP, DFP"

---

### Post by racepics on 2007-02-03
> **chipmonk010 said:**
> Try removing all the options in your devices section and copy/paste this in:

Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"
Option "UseEdidFreqs" "True"
Option "Metamodes" "1440x1050, 1440x1050"
Option "UseDisplayDevice" "DFP, DFP"

i still get twinview at 800x600 screens. but I installed an app called "resapplet" which allows me to change it to the correct res after booting. 

cheers

---

