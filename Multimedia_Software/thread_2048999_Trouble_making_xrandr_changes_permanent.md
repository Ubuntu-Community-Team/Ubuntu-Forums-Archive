---
title: "Trouble making xrandr changes permanent"
date: 2012-08-27
forum: Multimedia Software
---

### Post by edwpolanco on 2012-08-27
Hello there, I'm new to the hole linux environment (save for a few days years ago), and by both tweaking and searching the web for info I've been able to set my external monitor (actually external LCD tv). 

I've been able to set said monitor by the use of xrandr, after adding the new resolution (modeline, addmode, output, etc... you probably know the drift) to 1280x768 it works perfectly (it's the actual resolution of the monitor). The problem comes when its time to set the mode to be made permanent... 

I had a lot of trouble getting the info to make the xorg.conf file that I'm supposed and after creating and putting in a few things like the xrandr wiki said I'm left with the same startup setup as the time I first connected the monitor itself.

My video card (acording to the terminal) is:  Intel Corporation N10 Family Integrated Graphics Controller

And the xorg file I made and put into the ext/x11/xorg.conf has the following content:
```
Section "Monitor"
    Identifier      "Configured Monitor"
    Modeline        "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
    Option          "PreferredMode" "1280x768_60.00"
EndSection

Section "Device"
    Identifier      "Configured Video Device"
    Driver          "intel"
EndSection

Section "Screen"
    Identifier      "Primary Screen"
    Device          "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x768"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection
```

As a last note, the distro I'm using is UBUNTU 12.04 and I've changed the desktop environment to XFCE as unity was taking to much from the old netbook that I have, I'm not sure if that changes in any way the process of the setup.

Any help appreciated and thanks in advance...
- EdwPolanco

---

### Post by Zvezdica27 on 2012-08-28
hi,

xrandr and xorg.conf are rather advanced... no need to use them for the job, just use monitors (now displays) - press Ubuntu key, type monit... and the icon should come up.

Set the parameters you wish and when happy make the settings default.

Off course all this still uses xrandr, but is much more simple (GUI), made for us linux noobs.

zz

---

### Post by teledyn on 2012-09-28
this is perhaps related: under 11.10 and earlier, I could use randr -o left to flip my Gnome screen for my rotating monitor (essential for reading music scores) but in 12.04, under Unity, this technique no longer works

it works, but only for an instant, and then it quickly reverts to the portrait mode.  If I use the control-panel desktop admin tool the flip will work and stay, and if I edit xorg.conf it will stay, but these methods are too awkard for switching back and forth as I'd done in previous Ubuntu versions.

As of Ubuntu 12.05, it seems the xrandr method is broken under Unity, and I notice that the gnome-randr-applet and grandr are both now missing from the apt-get catalogs; I had cobbled my own shell script to do the flip but since randr won't stick, it's no longer useful :(  -- Anyone have any ideas what might be thwarting this approach? I thought it might be a known bug but so far I haven't had any luck locating a candidate bug report, and I'm not sure myself where to place it (nvidia?)

---

