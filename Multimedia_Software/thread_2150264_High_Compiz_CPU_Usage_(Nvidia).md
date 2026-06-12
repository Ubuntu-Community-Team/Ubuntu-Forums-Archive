---
title: "High Compiz CPU Usage (Nvidia)"
date: 2013-05-31
forum: Multimedia Software
---

### Post by svtguy88 on 2013-05-31
Well, I haven't posted around here in a while, but I'm running into an annoying problem that I can't seem to sort out.

I have an i5-3470, GT640 and 16 GB RAM.  The system was using Nouveau, but I was having crazy instability problems (panics) in both Ubuntu (Unity 2D or 3D) and Cinnamon.  I switched to the binary blob Nvidia driver, and I don't seem to get panics, but X and/or compiz will hog a LOT of my CPU time on core 0 (like ~60-80% when moving things around, about ~20% idle).

Right now, I've resorted to the Gnome fallback session, as it seems to perform the best in my situation, but what gives?  I am running three 1080p monitors, and I know the GT640 is no beast, but this machine should be _way_ more than capable...

---

### Post by gordintoronto on 2013-05-31
It's always useful to say what version of Ubuntu you are using. Also, which Nvidia driver? (nvidia-current works for me.)

---

### Post by Yellow Pasque on 2013-06-01
It sounds like 3D's not working correctly. Post your /var/log/Xorg.0.log

---

### Post by svtguy88 on 2013-06-19
Sorry for the long delay.  I've been using Gnome fallback, as I haven't really had the free time to debug this properly.

Anyway, I logged into Cinnamon (3d) for the first time in a while, and the problem seems to be fixed.  I'm using Xorg-edgers nvidia drivers, so who knows...something could have gotten patched/fixed somewhere.

I am having another problem though...I'll probably make a new thread for it if I don't get a response here.  My system will freeze (as in I can't even get to a TTY to kill things) from time to time.  Xorg's log looks fine at first glance (it just happened a few minutes ago), but my syslog shows "NVRM: Xid"errors, which, according to some googling, are definitely Nvidia driver errors...

---

### Post by svtguy88 on 2013-06-19
Ok.  System just froze again, and this is the last few lines of Xorg.0.log.old:

```
[  1839.504] [mi] Increasing EQ size to 512 to prevent dropped events.
[  1875.225] (WW) NVIDIA(0): WAIT (2-S, 17, 0xdeadbeef, 0x0000dbbc, 0x0000dc38)
[  1882.225] (WW) NVIDIA(0): WAIT (1-S, 17, 0xdeadbee
```

And yes, the last line just stops there without any more hex values or a closing parenthesis...

What's funny is that this time my syslog doesn't show any recent NVRM XID errors (none since the last reboot).  What the hell?  I'd say hardware problem (video card), but it's rock solid in Windows...or it was.  Maybe it's time to do some stress testing in Windows...

**edit** Well, I basically just watched it crash.  Everything began to move slowly -- dragging windows was choppy, then a few seconds later my music started stuttering, and then it all froze.  I had syslog open when it happened, and it was filling with NVRM XID errors.  I'm going to move back to nvidia-current, and if that still freezes, I'll likely go back to nouveau.  If I have time, I'll do some stress testing in Windows later tonight.

---

