---
title: "Custom resolution with Intel945 on mac mini?"
date: 2008-09-29
forum: Multimedia Software
---

### Post by anville on 2008-09-29
Hi all,

I have my Mac mini running Hardy (dual-booted) connected to my Philips HDTV.  There is an overscan problem, where part of the desktop is cropped. Under Mac OS X, I was able to set a custom resolution (using SwitchResx) and it works great.  Under linux, I have tried to add modeline definitions to the xorg.conf do the same thing, but I can never get a custom resolution at all.  It always goes to 1280x720.  

It's an Intel 945 graphics adapter.  Since Mac OSX can do it, I know the hardware is capable, but what I'm wondering is **if the Linux/X-Window driver can set custom resolutions?**.  It's certainly possible that I am not setting things up right.  I will post some excerpts from my org.conf below.


```

Section "device" #
        Identifier      "device1"
        Boardname       "Intel 945"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  0
        Vendorname      "Intel"
EndSection
Section "monitor" #
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
 modeline  "1216x676" 74.25 1216 1358 1398 1650 676 703 708 750 +hsync +vsync

        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
Section "screen" #
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Virtual 1280    720
                Modes           "1216x676" "1280x720@60"       "1280x720@50"   "1280x768@60"   "1280x800
@60"    "1280x854"      "1152x768@54"   "800x600@60"    "800x600@56"
        EndSubSection
EndSection


```

Any ideas?

---

### Post by prshah on 2008-09-29
> **anville said:**
> 
Under Mac OS X, I was able to set a custom resolution (using SwitchResx) and it works great.  Under linux, I have tried to add modeline definitions to the xorg.conf do the same thing, but I can never get a custom resolution at all.  

Take a look at [915resolution]("https://help.ubuntu.com/community/i915Driver"). It's available from the repos. Don't be mislead by the name, it works for all 8xx and 9xx series of Intel graphics cards / chipsets.

---

### Post by anville on 2008-10-01
Whoops.  I wrote Hardy, but I guess at this point I have Intrepid, which is still beta, and the 915resolution app isn't available now in apt.   Bummer. 

The funny thing is that the video driver's description includes the word "mode-setting," so I *must* be doing something wrong....

---

### Post by anville on 2008-10-07
OK, so I tested the custom modeline (1216x676) with an old laptop with Ubuntu, and it worked great!  So... the original question stands (slightly changed):

Can the X server Intel graphics driver on Intrepid actually handle custom modelines.  Do I need some special settings in the xorg.conf.  The 915resolution tool does seem to exist anymore, so I can't even play with it.  

Help! ( :) )

---

### Post by anville on 2009-10-30
Wow just found an old thread I started a year ago!  I just installed  Karmic 9.10 on my Mac mini, and was trying this out again.

The good news is that I was able to get custom resolutions working with the current driver by using xrandr:

```
xrandr --newmode 1216x676 74.25 1216 1358 1398 1650 676 703 708 750 +hsync +vsync
xrandr --addmode DVI1 1216x676
xrandr --output DVI1 --mode 1216x676
```

Now that I know the driver can handle it, I want to get this into a custom xorg.conf.  I tried to make a custom one, but can't get it right.  Does anyone have an example of a modern xorg.conf file for Ubuntu that will minimally configure a custom modeline?

Thanks!

---

### Post by anville on 2009-11-04
Solved!

My xorg.conf file needed to refer to the monitor label that already existed.  In my case it was "DVI1", which I got if I ran "xrandr"

So here is my entire xorg.conf file now:

```

Section "Monitor"
    Identifier      "DVI1"
    Modeline        "1216x676" 74.25 1216 1358 1398 1650 676 703 708 750 +hsync +vsync
    Option          "PreferredMode" "1216x676"
EndSection 
```   

I still have access to the standard resolutions that are detected, and the new one is just added to the mix.

*Finally* Ubuntu looks good on my TV!

---

