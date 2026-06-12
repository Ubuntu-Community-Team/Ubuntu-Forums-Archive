---
title: "Neomagic NM2160 (MAGICGRAPH 128XD) 1024x768"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by dannyboy79 on 2006-09-14
PLEASE PLEASE, HELP ME,
I have been just excepting this problem for too long now. I turned to linux about 3 monthes ago. I have Ubuntu on a desktop and Xubuntu on my old laptop. It's a Hitachi Pentium MMX with 128mb RAM. Anyway, I have been reading tons of forums and people have been saying that it's an Ubuntu problem that I can't get 1024x768. I also see that XF86 X server works with this Video chipset and having 1024x768. I have tried changing the Default Depth all the way down to 4 and still 1024x768 won't show up in the resolution list??? What else can I do to get this to work. Here is my relevant  xorg.conf
Section "Device"
        Identifier      "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
        Driver          "neomagic"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
        Mode    0666
EndSection

This is what ddcprobe states:
 sudo ddcprobe
vbe: VESA 2.0 detected.
oem: MagicGraph 128XD 40K SVGA BIOS
memory: 1920kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 320x200x32k
mode: 320x200x64k
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid:
edidfail
Can someone please help, I can't imagine that no one else has this video chipset when it's probably the main chipset in tons of computers!

Thanks,
dannyboy79

---

### Post by ske1fr on 2006-09-15
Wow, I thought I'd just be a spectator in these fora but here's another I can answer!

Not tons of computers but it can be the graphics chip in laptops of a certain age.  I've got an old Siemens Nixdorf Mobile 510 laptop with exactly the same graphics chip.  You can't get 24 or 32 bit colour at 1024x768 but you can get 16 bit at 1024x768, and here's how.

In xorg.conf the section ```
Section "Device"
Identifier "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
Driver "neomagic"
BusID "PCI:0:2:0"
EndSection
```should look like this:```
Section "Device"
Identifier "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
Driver "neomagic"
BusID "PCI:0:2:0"
Option "XaaNoScanlineImageWriteRect"
Option "XaaNoScanlineCPUToScreenColorExpandFill"
EndSection
```
Leave the default depth just the way you posted.  Save and restart.  The above lines come from [this Xfree86.org page](http://www.xfree86.org/current/neomagic.4.html), but the settings are valid in X.Org too.

Enjoy!:biggrin:

PS: have you got the ESS1869 audio chip in yours?

---

### Post by dannyboy79 on 2006-09-22
No, I have a Yamaha sound device I am pretty sure.

---

