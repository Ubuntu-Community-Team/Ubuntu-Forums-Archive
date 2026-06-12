---
title: "Valid NTSC 720x480 X modeline"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by Levander on 2007-11-17
I've got someone on another forum helping me get HD480i output from my TVOut port on my graphics card.  He says I need a NTSC valid 720x480 modeline.  I'm googling all over the place but can't find one.  Anybody can help a brother out?

---

### Post by mc4man on 2007-11-17
Modeline................ "720x480" 27.000 720 736 798 858 480 489 495 525 -hsync -vsync

---

### Post by Levander on 2007-11-17
Thanks mc4man, I'm about to try it out now.  

How do you know it's an NTSC valid one?

---

### Post by raydude on 2007-12-01
I don't know if anyone else will find this useful here, but i found this thread looking for a solution so maybe someone else will as well.

I got TV out working as primary output with xorg and a Radeon 9200.

I believe you have to be running the latest xf86-ati-driver and the latest xrandr for this to work.

Note this is the versions I'm running (all under gentoo):

```
equery list xorg
[ Searching for package 'xorg' in all categories among: ]
 * installed packages
[I--] [  ] app-doc/xorg-docs-1.4-r1 (0)
[I--] [  ] x11-base/xorg-server-1.3.0.0-r2 (0)
[I--] [  ] x11-base/xorg-x11-7.2 (0)
```

```
equery list ati
[ Searching for package 'ati' in all categories among: ]
 * installed packages
[I--] [ ~] x11-drivers/xf86-video-ati-6.7.196-r1 (0)
```

```
equery list xrandr
[ Searching for package 'xrandr' in all categories among: ]
 * installed packages
[I--] [  ] x11-apps/xrandr-1.2.2 (0)
```

The trick is to force the VGA output on, even when the VGA monitor isn't connected. You also have to force the modeline for 800x600 as it won't be auto detected correctly unless a VGA monitor is connected.

I got the modeline by grabbing it out of /var/log/Xorg.0.log.

```
Section "Module"
    Load        "dbe"   # Double buffer extension
    SubSection  "extmod"
       Option      "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
    Load        "freetype"
EndSection

Section "Files"
    FontPath   "/usr/share/fonts/misc/"
    FontPath   "/usr/share/fonts/Type1/"
    FontPath   "/usr/share/fonts/100dpi/"
    FontPath   "/usr/share/fonts/75dpi/"
EndSection

Section "ServerFlags"
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    Driver      "kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"   "xorg"
    Option "XkbModel"   "pc104"
    Option "XkbLayout"  "us"
EndSection

Section "InputDevice"
    Identifier  "Mouse1"
    Driver      "mouse"
    Option "Protocol"    "Auto" # Auto detect
    Option "Device"      "/dev/input/mice"
    Option "ZAxisMapping"   "4 5 6 7"
EndSection

Section "Device"
        Identifier      "Radeon 9200"
        Boardname       "ATI Radeon"
        Busid           "PCI:3:0:0"
        Driver          "radeon"
        Vendorname      "ATI"
        Option          "Monitor-VGA-0"         "VGA Monitor"
        Option          "Monitor-S-video"       "S-Video Monitor"
EndSection

Section "Monitor"
        Identifier      "VGA Monitor"
        Vendorname      "LG"
        Modelname       "CRT 1280x1024"
        Option          "DPMS"
        Option          "PreferredMode" "800x600"
        Option          "Enable" "true" # force vga on, this is necessary.
        HorizSync       30-96
        VertRefresh     50-160
       #force VGA to the same resolution as S-Video
        Modeline "800x600" 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync
EndSection

Section "Monitor"
        Identifier      "S-Video Monitor"
        Vendorname      "Unknown"
        Modelname       "TV or Beamer"
        Option          "DPMS"
        Option          "Enable" "true" # Force S-Video on, it is not detected correctly
       # Force the 800x600 modeline. THIS IS THE ONLY MODE FOUND TO WORK.
        Modeline "800x600" 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9200"
        Defaultdepth    24
        Monitor         "S-Video Monitor"
        SubSection "Display"
                Depth   24
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Keyboard1"
        InputDevice     "Mouse1"
#       Option          "AIGLX" "true"
EndSection

# Section "DRI"
#    Mode 0666
# EndSection

```

I hope someone else finds it useful.

Raydude

---

