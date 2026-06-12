---
title: "Nvidia FV43 Gforce 6200 xorg.conf help"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by w4ett on 2007-08-07
I installed the driver for my Nvidia 6200 card using Envy, and need for some kind soul to post their xorg.conf file so I can do some tweaking to get it to work properly.....image and window rendering are way off, and since this is my first Nvidia card (always used ATI in the past),  and I need a point in the right direction!!!  Many thanks in advance ](*,)

EDIT:  (How could I forget this?!?!)  Here are the applicable section from my xorg.conf  modified by nvidia-xconfig


> Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection


Section "Device"
    Identifier     "Nvidia Geforce 6200"
    Driver         "nvidia"
EndSection

---

### Post by w4ett on 2007-08-07
Sorry..it was late last night when I posted the card info should have read NV43 GeForce 6200.

lspci:

> 01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)

Don't let the lspci identifier confuse you...it IS a 6200 card (sticker on card and Nvidia bios message at bootup confirm the ID....I am running the card with the vesa driver now.  I asked on the #nvidia  irc channel, and apparently these 6200 agp cards were built around the 6600 card gpu.

Additional info: card will not run the live cd with the default settings...but will run in safe graphics mode.

---

### Post by tseliot on 2007-08-08
I think you should ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

