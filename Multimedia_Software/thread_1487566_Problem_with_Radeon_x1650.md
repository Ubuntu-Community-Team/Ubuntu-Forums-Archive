---
title: "Problem with Radeon x1650"
date: 2010-05-19
forum: Multimedia Software
---

### Post by undefiened on 2010-05-19
Hello,
At first excuse me for my bad english, this is not my native language.
I had a very slow perfomance at my card ati x1650.
In glxgears i have 3 fps in full-screen-sized window, but in small size i have ~1300 fps. I try to use "radeon" and "ati" driver, but it is no difference. If i try "radeonhd" driver, desktop don't loading (In gnome i enter password, and after i have white screen and cursor). Adding radeon modeset=0 or radeon nomodeset=0 don't working too.
glxinfo:
```
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV530
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
```

xorg.conf:
```
Section "Screen"
   Identifier   "Default Screen"
    SubSection "Display"
        Depth   24
        Modes   "1280x1024"
    EndSubSection
EndSection

Section "Device"
	Identifier      "Configured Video Device"
        Driver          "radeon"
EndSection

Section "Monitor"
   Identifier   "Configured Monitor"
EndSection

```

---

### Post by Tomi Neste on 2010-05-21
I can't help but I do have similar problems.

I have been using the OSS Radeon drivers (latests from xorg-edgers repo) with my x1200 and it was very slow with 9.10 and after updating to 10.04 it is now _very_ slow. I get ~300fps on windowed glxgears and 20fps in fullscreen. There is something very wrong here, with some test I have made Vista is over 10 times faster, under 9.10 it was still just 2-5 times faster.

In addition there randomly appears ~10 pixel wide black lines in opengl surfaces.

Edit: Seems that [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/544496](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/544496) might be related to this. Except that I don't have any problems with UI or video playback speed (which seems weird).

---

### Post by undefiened on 2010-05-22
In windowed i have 1000 fps, but in fullscreen i have 2-3 fps, and cursor freezes, then i move it to close.

---

