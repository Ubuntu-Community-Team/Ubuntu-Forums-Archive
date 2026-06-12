---
title: "S-video out to Tv with an ATI card"
date: 2009-10-06
forum: Multimedia Software
---

### Post by aaeellxx on 2009-10-06
hi everybody

i have a Tv card ATI 9200 se  and i try to conect to the tv by S-video

but i have a problem, the tv inst detected by the OS, but when the pc start(BIOS),  the TV works and the splashscreen too, and the terminal tty 1,2,3,4,5,6 works too, but with problem, the video is distorted in all of this..

it dont works in the graphic system the tv signal stops when entert to GDM and gnome

if some body could helpme please 

a xorg problem i think

ubuntu 9.04
ati 9200 se

---

### Post by aaeellxx on 2009-10-07
any help over here?

---

### Post by jim258kelly on 2009-10-08
I don't think I had the same problem as you.

But this wiki helped me out:

[http://wiki.archlinux.org/index.php/ATI#TV_out](http://wiki.archlinux.org/index.php/ATI#TV_out)

---

### Post by aaeellxx on 2009-10-10
Thanks i solved

only changing the xorg.conf

```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "radeon"
    Option        "TVStandard" "ntsc"
    Option        "ForceTVOut" "True"
    Option        "TVDACLoadDetect" "True"
EndSection
```

now i dont know how to change the screen resolution

and this is my xorg of the screen section:

actualy i have 800x600.... : (

```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth     24
    SubSection "Display"
        Depth    1
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    4
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    8
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    15
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth    24
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

any help???

---

