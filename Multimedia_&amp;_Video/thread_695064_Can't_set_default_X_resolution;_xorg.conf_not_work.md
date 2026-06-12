---
title: "Can't set default X resolution; xorg.conf not working"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by aseering on 2008-02-12
My display supports 1680x1050; in order to get this resolution to work at all, though, I had to add a modeline to xorg.conf.

After adding the modeline, I can switch to the higher resolution, but the login screen defaults to 1280x720 (as do new accounts).  Is there a way to change this?

I have a "Modes" entry in xorg.conf as follows:

```

Section "Screen"
(...)
    DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth 24
        Modes "1680x1050" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

I have a Radeon X300 graphics card.  I'm using the "radeon" driver because the "fglrx" driver causes X to wedge.

---

### Post by xzero1 on 2008-02-12
I had a similar problem and had to misidentify my monitor in xorg in order for it to work correctly. Make sure you back up your old xorg.conf before doing this type of thing. Check your xorg log file and it may give you a clue what is happening.

---

### Post by aseering on 2008-02-12
I've checked my xorg log file; no useful information (ie., no errors, nothing interesting referring to the resolutions in question).

I could post the whole log file; would that be useful?

What do you mean by "misidentify your monitor"?

---

### Post by xzero1 on 2008-02-13
After upgrading my monitor (samsung 216bw) I could not get 1680x1050 on bootup. The log showed that my selected resolution was 'tried' and would then fallback to a lower resolution.  My old monitor could do 1600x1200 so I used my old backed up xorg.conf, booted up and it worked. I edited the new xorg.conf to include the modes that my 216bw could use, removed those it couldn't  and have had no problems since.

Here are the relevant sections:

```
Section "Monitor"

#Option		"DPMS"
# 2048x1536 @ 70.00 Hz (GTF) hsync: 111.93 kHz; pclk: 315.19 MHz
    Identifier     "DELL P1110"
    ModeLine       "2048x1536_70.00" 315.2 2048 2208 2432 2816 1536 1537 1540 1599 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "DELL P1110"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

The critical info is clearly the modeline. Notice I have a nvidia card. 
USE AT YOUR OWN RISK! 
Good luck.

---

### Post by AceRimmer on 2008-02-14
I bought a LG 226 WTQ 22" last night and it tells me the signal is not in range when I try to boot it up.  I'm using an ATI X800GTO card, when I had it hooked up to the Geforce 2 MX card on another system it worked ok.  I'll try editing the xorg.conf

---

### Post by aseering on 2008-02-15
Hm...  Adding a modeline like that doesn't help.

Does anyone know how the radeon driver actually chooses either its default resolution, or the set of resolutions that one can select from?  Neither the list nor the default seem to correlate at all with anything in xorg.conf...

---

### Post by xzero1 on 2008-02-17
This thread should help:
[http://ubuntuforums.org/showthread.php?t=696269]("http://ubuntuforums.org/showthread.php?t=696269")

---

