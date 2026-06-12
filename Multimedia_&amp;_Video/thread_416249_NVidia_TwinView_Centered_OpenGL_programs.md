---
title: "NVidia TwinView Centered OpenGL programs"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by zaf on 2007-04-20
I have what seems like a simple problem.
I have a NVidia (using the nvidia proprietary driver) TwinView setup, with two LCDs running at 1280x1024 side by side.

The Window Manager understands this and correctly maximizes applications to one screen or the other.

When I run OpenGL programs in full screen mode, most unfortunately center themselves between my two monitors. (eg the left half of the program appears on the left monitor, and the right half on the right).

This is obviously somewhat annoying.

Is there any way to convince an OpenGL program to display only on one monitor?

I have tried googling the problem, but can't come up with the right terms to produce meaningful results.

Thanks

**Update - Solved**

Ok, solution was relatively easy.
Edit /etc/X11/xorg.conf

Find the "Screen" section
Change the metamodes option:
My metamodes option looks like this
Option "metamodes" "1280x1024,1280x1024; 1280x1024,NULL"

Restart the X server (Ctrl+Alt+Backspace), and it works.

Adding the 1280x1024,NULL mode seems to allow OpenGL apps to use just the left screen. (Obviously if you use this solution, change the resolutions to match your monitors.

Thanks

---

### Post by Wooksta on 2007-04-29
Just wanted to say thanks, i've been searching for this solution for months without any luck, much appreciated!

:KS 

Cheers,
Wooksta

---

### Post by jondecker76 on 2007-04-29
much thanks, this has helped me also!

---

### Post by Hobo Joe on 2007-06-01
My meta mode section looks like this:
```

Option         "metamodes" "CRT-0: 1152x864 +1152+0, CRT-1: 1152x864 +0+0; CRT-0: nvidia-auto-select +800+0, CRT-1: 800x600 +0+0; CRT-0: nvidia-auto-select +640+0, CRT-1: 640x480 +0+0"

```
As you can see, it's pretty drastically different than the one you posted.

I'm running both monitors at 1152x864. If someone could perhaps make a metamode option for me, that would be fantastic.

---

### Post by Hobo Joe on 2007-06-01
Ok, I got it working, but I ran into some weird problems. When I try to run a game in WINE, WC3 for example, it runs fine on one of my monitors, but the other one goes black, and then if I exit the game, my desktop is all messed up, as if it tries to fit my whole dual monitor desktop onto one monitor, meanwhile, the other monitor is still turned off. 

A quick reboot fixes it, but still, it's really annoying.

Also, when I try to run a steam game, it crashes.

---

### Post by Gruelius on 2007-06-14
have you tried CTRL + ALT + BACKSPACE?

im going to see if this fixes my steam problem. BTW you could just ditch twinview for seperate screens :P a bit of a performance hit tho.

---

