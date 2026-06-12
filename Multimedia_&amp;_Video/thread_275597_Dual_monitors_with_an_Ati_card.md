---
title: "Dual monitors with an Ati card"
date: 2006-10-11
forum: Multimedia &amp; Video
---

### Post by Drakonik on 2006-10-11
I'm running Dapper Drake with GNOME, and using an Ati 9550. I've got two monitors, with one plugged into head. The problem is that the second screen only mirrors the first.

I've seen all kinds of hacks for the xorg.conf file that crashed my system or just stopped it from booting. What can I do?

---

### Post by lokalhost on 2006-10-11
So far the best method I've found of dealing with the ATI problem is presented here: [http://www.ailis.de/~k/docs/atilinux/]("http://www.ailis.de/~k/docs/atilinux/")

It did not get my 3D up and running completely; but after I did a few apt-get updates and a apt-get dist-upgrade my 3D finally kicked in.

---

### Post by Drakonik on 2006-10-11
That guide doesn't work anymore, or at least not with the drivers I'm using. Anything else?

---

### Post by lokalhost on 2006-10-11
I bookmarked all the pages I used for reference, I'll link them below in case there is something you haven't come across yet.

[http://www.stanchina.net/~flavio/debian/fglrx-installer.html#install]("http://www.stanchina.net/~flavio/debian/fglrx-installer.html#install")

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25")

[http://www.ubuntuforums.org/showthread.php?t=24557]("http://www.ubuntuforums.org/showthread.php?t=24557")

[http://gentoo-wiki.com/HOWTO_ATI_Drivers]("http://gentoo-wiki.com/HOWTO_ATI_Drivers")

I added some of the repositories and packages suggested in this shell script:

[http://www.kde-apps.org/content/show.php?content=43320]("http://www.kde-apps.org/content/show.php?content=43320")

If none of these help you out, post your xorg.conf and any meaningful snippets from your xorg log along with what you've tried already.

---

### Post by lokalhost on 2006-10-11
Here are my relevent settings for a "Big Desktop" (I am living with the vertical mouse position bug from having displays at different resolutions).

```

Section "Module"
       #Add for 3d:
       Load "GLcore"
       Load "glx"
       Load "dri"
       # Load "extmod" but omit DGA extension
       # (the DGA extension is broken in the fglrx driver)
       SubSection "extmod"
         Option "omit xfree86-dga"
       EndSubSection
       #
       Load  "i2c"
       Load  "bitmap"
       Load  "ddc"
       Load  "extmod"
       Load  "freetype"
       Load  "int10"
       Load  "type1"
       Load  "vbe"
       Load  "dbe"
       Load  "v4l"
EndSection
```

```

#Section "ServerFlags"
#       Option      "Xinerama" "true"
#EndSection
```

```

Section "Monitor"
       Identifier   "Monitor[0]"
       VendorName   "Generic"
       ModelName    "Flat Panel 1440x900"
       HorizSync    31.5 - 100.0
       VertRefresh  59.0 - 75.0
       Gamma        1
       ModeLine     "1440x900@60"   96.21  1440 1504 1536 1760  900 903 906 912 -hsync +vsync
EndSection
```

```

Section "Device"
       Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
       Driver      "fglrx"
       BoardName   "ati"
       Option      "VideoOverlay" "on"
 #       Option          "UseFBDev"              "true"
       Option      "OpenGLOverlay" "off"
       Option      "UseInternalAGPGART" "no"
       BusID       "PCI:1:5:0"
       Option "DesktopSetup"  "horizontal,reverse"
       Option "Mode2"         "1280x1024"
       Option "ForceMonitors" "lvds,crt1"
EndSection
```

```

Section "Screen"
       Identifier "Screen[0]"
       Device     "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
       Monitor    "Monitor[0]"
       DefaultDepth     24
       SubSection "Display"
               Virtual 1280 1024
               Depth     24
               Modes    "1440x900@60"
       EndSubSection
EndSection
```

```

Section "Extensions"
       Option "Composite" "Disable"
EndSection
```

---

