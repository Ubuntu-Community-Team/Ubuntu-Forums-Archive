---
title: "Screensaver preview appears in front of other windows."
date: 2009-04-02
forum: Multimedia Software
---

### Post by Rinnan on 2009-04-02
I'm running into a strange 3D problem.  It has been a problem with Intrepid and remains a problem with Jaunty.  

Hardware;  Intel 945 video, Toshiba laptop.

If I run the screensaver preferences window, and set it to preview a 3D screensaver, such as queens, and then drag another window in front of it, the actual screensaver preview will _remain_ in front of all other windows and obscure the window that should be covering it!  The rest of the screensaver preference window will however be correctly behind the frontmost window, only the actual preview area itself will be incorrectly in front.

Has anyone seen this before?  I checked launchpad, but didn't find anythign with the search terms I used (screensaver preference window in front, and some others).  This might have shown up in various ways causing people to report it using different words.

It's too bad because so much improved in Jaunty graphics in other ways, such as the fact that in Jaunty, full screen 3D programs no longer flicker if something 3D behind them is updating.

---

### Post by Rinnan on 2009-04-02
More information:  setting the "UXA" setting in my xorg.conf fixes this, but now X crashes occasionally.  Strange choice, I have to pick between buggy and slow, on the one hand, and fast and very unstable on the other.  Awful.

The problems that uxa fixes are:

Wrong "z-order" (so to speak) of OpenGL portions of some windows (e.g. screensaver)
Slow and not smooth
Jerky and unstable full-screen flash

Hm.  Can't I have my cake and eat it too!!? :p

---

