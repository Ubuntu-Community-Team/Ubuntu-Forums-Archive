---
title: "[mythbuntu] X won't come up when power cycle TV"
date: 2014-05-02
forum: Multimedia Software
---

### Post by moriarty00 on 2014-05-02
Hey, all. I'm running a Mythbuntu server, which I just upgraded from 13.10 to 14.04.  I use a TV as my monitor.  Ever since the upgrade, if I turn the power to the TV off and then back on, X doesn't come back up. The TV does not register a signal from the computer.  If I switch to a different console (with ctrl+alt+F5 or whatever) and restart X (sudo service lightdm restart), it comes right back up. But I don't want to have to do this every time!  Any thoughts?

It may be relevant that the upgrade seems to have removed my /etc/X11/xorg.conf file. However, when I restored it, that didn't fix the problem. (I don't remember writing most of that file; much of what's in there, especially the "TripleBuffer" thing, is probably suggestions from the MythTV list in response to video problems I was having.)

Here's my xorg.conf:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Extensions"
        Option  "Composite"     "Disable"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "TripleBuffer"  "True"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
EndSection

```

Exerpt from /var/log/Xorg.0.log :

```
[when I turn the TV off]
[105604.311] (II) NVIDIA(0): Setting mode "NULL"

[when I turn the TV on]
[105622.792] (II) NVIDIA(GPU-0): Display (BBY HDMI (DFP-1)) does not support NVIDIA 3D Vision
[105622.792] (II) NVIDIA(GPU-0):     stereo.
[105622.792] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[105622.792] (**) NVIDIA(0):     device BBY HDMI (DFP-1) (Using EDID frequencies has been
[105622.792] (**) NVIDIA(0):     enabled on all display devices.)
[105622.794] (WW) NVIDIA(GPU-0): The EDID for BBY HDMI (DFP-1) contradicts itself: mode
[105622.794] (WW) NVIDIA(GPU-0):     "720x480" is specified in the EDID; however, the EDID's
[105622.794] (WW) NVIDIA(GPU-0):     valid HorizSync range (31.000-69.000 kHz) would exclude
[105622.794] (WW) NVIDIA(GPU-0):     this mode's HorizSync (15.7 kHz); ignoring HorizSync check
[105622.794] (WW) NVIDIA(GPU-0):     for mode "720x480".
[105622.831] (II) NVIDIA(GPU-0): Display (BBY HDMI (DFP-1)) does not support NVIDIA 3D Vision
[105622.909] (II) NVIDIA(GPU-0):     stereo.
[105622.942] (II) NVIDIA(GPU-0): Display (BBY HDMI (DFP-1)) does not support NVIDIA 3D Vision
[105622.942] (II) NVIDIA(GPU-0):     stereo.
```

Thanks in advance for any help you can offer!

---

### Post by dannyboy79 on 2014-05-02
this post should be what you're looking for [http://ubuntuforums.org/showthread.php?t=2200907](http://ubuntuforums.org/showthread.php?t=2200907)

---

### Post by moriarty00 on 2014-05-02
I added this:

```
       Option "ConnectedMonitor" "DFP-1"
       Option "UseDisplayDevice" "DFP-1"
```

to my xorg.conf, and everything works now! Thank you!!

---

### Post by dannyboy79 on 2014-05-02
awesome, glad I could help. please mark the thread solved.

---

