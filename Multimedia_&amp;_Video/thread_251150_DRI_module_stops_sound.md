---
title: "DRI module stops sound"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by ubuntuuser on 2006-09-05
Hi all,

after losing half of what's left of my hair I stopped trying to get the ATI drivers to work AND have sound at the same time. A few weeks passed, then I read somewhere that ATI had released version 8.28.8 of their drivers, and I decided to give it another try. I downloaded the installer binary, and it installed flawlessly. fglrxinfo told me I was using the ATI driver, not the MESA ones, everything was fine...but my sound didn't work again!!!

Whenever gdm starts, I can hear this "gdm ready"-drum sound, but it is played four times. When I login, I hear no startup jingle, and xmms tells me that my sound device is busy. I simply don't get no more sound at all.

Well, I felt ambitious this time and was eager to solve this problem. First I checked if any other process was occupying my sound card.```
ps aux | grep play
```told me that there were aplay and gdmplay running, so I killall'd them both. Now, xmms didn't tell me that my sound device, was busy, but instead of just playing my music, it repeated the first second of any song for about for times, then muted :evil:.

Long story short, I started an error tracking session and found out that my sound works when I remove the Load "dri" line from my xorg.conf.
So whenever I start X using that line, I can have 3D accel, but no sound. W/o that line, I have sound, but use the MESA driver. That problem exists since I installed Dapper, independent of the ATI driver version I tried.
Here is the relevant info:
```
Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
``` Here are some extracts from my xorg.conf:```
Section "Module"
        Load  "GLcore"
        Load  "i2c"
        Load  "bitmap"
        Load  "dbe"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

...

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 NP"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        BusID       "PCI:1:0:0"
        Option      "UseInternalAGPGART" "no"
EndSection

...

Section "DRI"
        Mode         0666
EndSection
``` I have no clue what's going on. I searched this forum and the rest of the web, looks like a pretty rare problem, cause I haven't found anything. Ideas, anyone?

---

### Post by ubuntuuser on 2006-09-06
Anyone?

---

### Post by ubuntuuser on 2006-09-09
Ok, now this is my last *bump* for this thread

---

### Post by redhed on 2006-09-26
I have the same problem :(

---

### Post by RSL on 2006-10-10
I'm running an ATI Radeon 9200 and the Intel integrated sound card and don't have any problem running the DRI and sound together. I'm even running beryl.

I _do_ have sound issues but I think they have to do with Amarok and Firefox not playing nice. [Perhaps it's just time to give up on Amarok.]

---

