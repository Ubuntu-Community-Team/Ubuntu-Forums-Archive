---
title: "Mplayer Error no Xvideo support"
date: 2006-07-22
forum: Multimedia &amp; Video
---

### Post by vjun on 2006-07-22
Hello everyone, I am having some problem playing xvid video.

I'm using Mplayer to play my video files, and I got rid of Totem. Anyway, Mplayer seems to be able to play xvid video but it's at another window which allowed me to press F (screen went white) or C (circle resolution seems to work).

What annoyed me is the error message whenever i open a video.

"It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read ....
"

Maybe these info could help you guys.. thanks in advanced.

~$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

and also part of my xorg.conf file.

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

---

### Post by CuBone on 2006-08-18
Did you find any solution? I'm having the same problem

---

### Post by whatever on 2006-08-18
```
sudo aticonfig --overlay-type=Xv
```

---

### Post by soop on 2006-10-20
Did this fix your issue?

---

### Post by gioachin on 2007-10-31
I had the same problem after I upgraded from Feisty to Gutsy.
I solved the problem by disabling the proprietary driver from ATI (found in the section about restricted drivers).
Now everything works again (and direct rendering/OpenGL is still enabled)

---

### Post by eye208 on 2007-11-01
The solution is to enable XVideo as shown in post #3.

Of course you can also switch to the open source driver instead, but then you will lose the ability to run games and other applications that require accelerated OpenGL 2.0 support.

---

