---
title: "Ati x1600 pro performance"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by acankat on 2006-06-24
I've an annoying performance problem with my x1600 pro agp card in dapper. 3d acceleration seems to work fine, but frame rates are far beyond than it should be.

Is there a good solution?:confused:

---

### Post by didobuntu on 2006-06-24
What they should be .. and what your fps with "glwgears -printfps" and with "fgl_glxgears" ?

---

### Post by acankat on 2006-06-25
about 1400 fps in glxgears.

I Can't play even bzflags fluently:(. 

ps: direct rendering is enabled and 8.25 driver is installed

---

### Post by disturbed1 on 2006-06-25
I have a couple of these cards :( 

It's a dog in Linux, about on par with an Nvidia FX5500 or an ATI 9600.

The video playback looks damn good though, but ATI did not enable the TV out on the x1xxx cards.

Drivers 8.24 were the first drivers to have support for the x1xxx series, 8.25 were a huge improvement, I noticed a 20-25% gain in performance. With 8.24, my FX5500 was actually much faster than the x1600, with 8.25 it puts the x1600 about on par with the FX5500 in Doom3 and Quake.

I'm waiting until the next driver update before I give these cards away and move on to all Nvidia cards. Considering 8.25 had a decent performance increase, and brought out AVIO (undocumented but it works for deinterlacing and color correction), I have hopes for the next release.

Here's a portion of my Xorg.conf, see if there's any differences, and give them a try to see if it helps.

```

Section "Device"
    Identifier  "ATI Technologies, Inc. RV530 x1600 Pro"
    Driver      "fglrx"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    Option        "TexturedVideo" "on"
    Option        "FSAAEnable" "on"
    Option        "FSAAScale" "4"
    Option        "FSAADisableGamma" "off"
    BusID       "PCI:1:0:0"
EndSection

``` 
```

~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon AVIVO Video"
    number of ports: 1
    port base: 83
    operations supported: PutImage

``` 
For Mame I had to add these options in also

```

Section "Module"
    Load  "i2c"
    Load  "bitmap"
    Load  "ddc"
    Load  "dri"
    Load  "freetype"
    Load  "glx"
    Load  "int10"
    Load  "type1"
    Load  "vbe"
###This is for xmame
 Load  "extmod" #for xmame to work
SubSection "extmod"
        Option "omit xfree86-dga" #Don't initialize the DGA extension
EndSubSection
###End xmame option
EndSection
```

---

### Post by acankat on 2006-06-25
Tx for the reply; I'll verify my xorg setting according to yours as soon as possible. I hope it makes some difference.

---

