---
title: "Max Texture Size? (Dual Monitor - Beryl AIGLX ATI)"
date: 2006-12-04
forum: Multimedia &amp; Video
---

### Post by MonsterX on 2006-12-04
So I played around with my xorg.conf today and got dual monitor beryl going, but I ran into a problem that I think is due to Max Texture Size

My primary is a dell 2407 and the secondary is a small lcd, the wall paper (and entire desktop really) wraps to only about 1/8th of the second monitor.

From everything I read this is due to max texture size of 2048.

What I want to know is that is this max texture size a software or hardware problem?  Can drivers be written that increase this size?  Does any hardware support greater than 2048 textures?

This is my first post to Ubuntu Forums,

Thanks in advance

---

### Post by lnaves on 2006-12-07
I have a radeon mobility ( "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]" ) and cannot get dual displays to work. Can you post the appropriate sections of your xorg.conf file?

---

### Post by mfeif on 2006-12-23
I can't answer your question, but I've seen the same kind of thing:

I have two side-by-side 1600x1200 displays, and anything OpenGL is garbage if I move it past the middle of the right screen (around the 2048 mark). I have a Radeon 9600.

I've seen message posts online that indicate that some newer cards could theoretically show up to 4096x4096 in 3d, but it seemed like the devs who were discussing that had never seen it.

For my part, I gave up with AIGLX on the dual-head, though I did get it working... but with only 1/3 of the second screen showing properly, it's not worth much.

Good luck.

---

### Post by scottDkoDer on 2006-12-29
Before getting my fglrx+ati+dual+beryl to work I had an interesting 'problem'.  Beryl thought it was running on two monitors on one screen.  So in other words if I would maximize a window it would only cover half the screen.  I fixed this by using BigDesktop mode except not specifying resolution modes in the device section but the screen section as follows:
Modes "1280x480" "1024x768" "800x600" "640x480"

Note that the first mode is 1280x480 not 1280x1024 and placing this in both screen sections allowed me dual-monitor mode at a resolution of 2048x768. The resolution right after the "1280x480" entry seems to dictate what the max dual-mode resolution is. (Don't ask me why.) :cool:

---

### Post by dhanson358 on 2007-01-05
I'm using FC6, not Ubuntu, but I think I am hitting this same issue.  I have a Radeon 9600 Pro using the 'radeon' driver with aiglx, beryl, and using MergedFB for dual head display.  Running 2560x1024, and about 2/3 of the way through the right-side monitor, the desktop just stops.  I can drag windows out there, but the get heavy tracers in the "void" area.  3d effects all work fine.

I know it was a pain to get just as far as I have, so I figure I'll put up my xorg.conf since I've got it all working except the texture size thing.  Nothing complex here at all, but it seems to work.

```

Section "Device"
        Identifier  "Videocard0"
        Driver      "radeon"
        Option "MergedFB" "true" 
        Option "CRT2Position" "RightOf" 
EndSection


Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        DefaultDepth     16
        SubSection "Display"
                Depth     16
                Modes    "1280x1024"
                #Virtual 2560 1024
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024"
                #Virtual 2560 1024
        EndSubSection
EndSection

                  

```

---

### Post by scottDkoDer on 2007-01-08
Try making your default depth 24? and/or removing the second 'SubSection' in the 'Screen' section??

---

### Post by xalen on 2007-02-07
I have exactly the same problem with the "void" area, seems to all work fine except my desktop doesn't work properly beyond 2/3rds of my second screen, but I also have no desktop, it's just white, I do have task bar.

Anybody got this working fully?

I've got an ATI card and I've briefly tried Xinerama with XGL+fglrx but Beryl doesn't work.  Not sure if XGL was set up correctly but fglrx was.  Tried BigDesktop but again that needs XGL+fglrx so same issue.  MergedFB is the closest I can get.

[IMG]http://oliverpolden.co.uk/images/snapshot1.png[/IMG]
[IMG]http://oliverpolden.co.uk/images/snapshot2.png[/IMG]

---

