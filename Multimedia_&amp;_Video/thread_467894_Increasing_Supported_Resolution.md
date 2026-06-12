---
title: "Increasing Supported Resolution"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by CybaCowboy on 2007-06-08
Hi,


My monitor supports a resolution of 1280x1024 in Microsoft Windows XP: Professional, which I assume is the maximum resolution considering Windows XP: Professional will not me select any higher, however Ubuntu 7.04 ("Feisty Fawn") only allows me to select a resolution of up to 1024x768, with a refresh rate of 85Hz!

On my 17-inch monitor, this makes things really cramped (especially when surfing), and it is heartbreaking going from 1280x1024 in Windows XP: Professional to 1024x768 in Ubuntu 7.04 ("Feisty Fawn")...


Anyway, As I know virtually nothing about monitors, I've copied the information directly from the Display Properties in Windows XP: Professional to help anyone that would be so kind as to help me increase the resolution in Ubuntu 7.04 ("Feisty Fawn"):
[i]
**General**
* Resolution: 1280x1024 pixels
* Color Depth: True Color (32-bit)

**Adapter**
* Adapter Type: Gigabyte RADEON 9200SE Series
* Chip Type: RADEON 9200 SE AGP (0x5964)
* DAC Type: Internal DAC (400MHz)
* Memory Size: 128MB
* Adapter String: Gigabyte RADEON 9200SE Series
* BIOS Information: BK-ATI VER008.015.028.000

**Monitor**
* Monitor Type: AOC Spectrum 7F
* Screen Refresh Rate: 60Hz
[/i]


Step-by-step instructions, where possible, would be greatly appreciated...


Thanks peoples!

---

### Post by ofek on 2007-06-08
You could edit xorg.conf - "sudo nano /etc/X11/xorg.conf"
and find the line of the screen resolution (in the screen section, should be near the end of the file) and in the 24bit (the line below Depth 24) section add "1280x1024" (with quoting marks) before the "1024x768" that's already there, Restart X and thing should look better =).

---

### Post by CybaCowboy on 2007-06-08
Worked like a charm!

Thanks!

---

### Post by NeilBlanchard on 2007-06-15
Greetings,

I am stuck at 800x600 (the only other resolution shown in preferences is 640x480) -- and yet my xorg.conf file has this:

> Device         "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor        "PV500"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection


Wassup 'wid dat?:confused:

---

### Post by SoloSalsa on 2007-06-25
> **NeilBlanchard said:**
> I am stuck at 800x600 (the only other resolution shown in preferences is 640x480) -- and yet my xorg.conf file has this:...I had the same thing (with proprietary drivers...).  I edited xorgconf myself, and did the terminal setup program, and mine just never worked above svga.  
I gave up with *any* acceleration, and reinstalled, and never chose proprietary settings.

---

### Post by NeilBlanchard on 2007-06-25
Hello,

I did get it working, using the directions elsewhere on these Forums:

> sudo dpkg-reconfigure -phigh xserver-xorg

Select the video driver, and use the Space Bar to select the resolutions that you want listed.

---

