---
title: "Ghost mouse on rotated screen (Karmic, ATI)"
date: 2009-12-07
forum: Multimedia Software
---

### Post by afoglia on 2009-12-07
We recently upgraded from 8.10 to 9.10, and I'm having display problems.  I have ATI Radeon HD 4670 card with the fglrx driver.  Before I was able to get XRandR working (unofficially supported by the driver), and have one of my two monitors rotated 90 degrees, with no problems.  Now whenever a monitor is rotated, there is a ghost mouse pointer on it.

This is similar to [bug 357901]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/357901"), but that bug occurred under Xinerama, and that bug was supposedly fixed in 9.10.  Also my problem is only when the monitor is rotated.

Under 8.10, I was running Gnome with metacity (the only combination that would work).  Under 9.10, I can now run compiz or kwin and get the 3-D effects, but I'd gladly give them up to lose the extra mouse pointer.  (The ghost mouse pointer also exists with metacity.)

Any suggestions?

---

### Post by jaksprats on 2009-12-28
I have the same problem
Running compiz on a Lenovo w500 on karmic, I have two monitors hooked up to it
one 2560*1600 which is ok
2nd external monitor is 1680*1500 rotated left.

If I move the mouse on the first screen (2560*1600) it shows up on the 2nd screen, IFF it is within the square (1680*1050) on the first screen .... e.g. the ghost mouse is not on the lower right hand corner of the first monitor. Similarly the ghost mouse's orinetation is off by 90degrees.

Unrotating the 2nd monitor "solves" this problem, but I need the 2nd monitor at 90 degrees.

I vaguely remember someway to adjust the mouse orientation using xrandr, i will look into it

---

