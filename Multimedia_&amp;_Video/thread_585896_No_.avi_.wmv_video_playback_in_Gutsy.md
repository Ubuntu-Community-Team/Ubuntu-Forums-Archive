---
title: "No .avi .wmv video playback in Gutsy"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by lazyart on 2007-10-21
Upgraded my laptop from Feisty to Gutsy.  Having no luck viewing videos in Totem, Xine or VLC.  I can hear the audio track but the video is just dark green output.  I don't believe I ever tried to play .wmv or .avi before the upgrade.  I installed the restricted formats from Add/Remove, as well as all the goodies from Medibuntu but still I get the green output.  w32codecs are installed.

Anyone know what I'm missing?

---

### Post by gotthardt on 2007-10-21
I wanted to add mine too. It worked fine in fiesty, but after moving to gutsy, I only see blue (overlay with nothing on it?). Sound is fine. This is for avi playback in totem. Also mythtv watching tv is all blue also. 

any help?

here is lspci for my vid card: 
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

xorg.conf:
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
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
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
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

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Screen  0
        Identifier      "ATI0"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection


#Laptop Display
Section "Monitor"
        Identifier      "Laptop Display"
        Option          "DPMS"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI0"
        Monitor         "Laptop Display"
        DefaultDepth    16
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
        Screen  0       "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection


Section "DRI"
        Mode    0666
EndSection

---

### Post by lazyart on 2007-10-21
Wow, what a coincedence.  I'm using the same vid card, same resolutions.  Evo N620c?

---

### Post by gotthardt on 2007-10-21
Mine is a thinkpad T30 - If the bug is only for us we may be in trouble - only a few of us... I might have to go back to feisty...
I will wait for a response and then post a bug later if we don't get any good advice.

---

### Post by gotthardt on 2007-10-22
Here is a bug from someone else with the same prob:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155157](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/155157)

---

### Post by joaopcrodrigues on 2007-10-22
:confused: Hi, got same problem here... with feisty everything was fine, beryl was cool,,, everything worked more or less fine, few bugs now and then. Now with Gutsy, had to spend hours to configure nvidia and xorg.conf to make compiz-fusion work. Though I managed ok, and compiz fusion is pretty cool, there is the 3Dwindows missing and the mouse on the corner to see all windows (I was used to those plugins). When I though everything was fine...NOW I CAN'T SEE AVI FILES.. :evil:.. come on... I have a dual core dua 2,24 and an nvidia 7600gt XFX with 1 Gb of ram.... every thing should work. 

joaopcrodrigues

P.S.: haven't tested vmware workstation yet... hope it still works...

---

