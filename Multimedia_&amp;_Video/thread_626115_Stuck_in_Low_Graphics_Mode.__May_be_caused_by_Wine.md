---
title: "Stuck in Low Graphics Mode.  May be caused by Wine"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by Envergure on 2007-11-28
I just installed Wine.  I ran Unreal Tournament 2004 for a few minutes, just to see if it would work and how fast it would run.  The mouse was stuck in the top two-thirds of the screen, which was at 640x480.  When I quit the display stayed at that resolution.  I got it back to normal, which took some doing as most of my panels were hidden.  I restarted X, which took longer than usual, and when it returned to the login screen it was in Low Graphics Mode because it didn't properly detect the video card driver, or something like that.

Any ideas?

In the mean time I'll try removing Wine, restarting, whatever I think of.


EDIT:
Uninstalling Wine didn't do it.  Now I get normal graphics as long as I don't enable the restricted driver for my video card.  If I enable it, the thing restarte in Low Graphics Mode..

---

### Post by Envergure on 2007-11-28
Never mind, I got it.

I went into "Configure" and chose a generic plug-n-play monitor driver.  I selected "ati - ATI Mach8, Mach16, Mach64, [something else]" for the video card driver.  I restarted, and it works.

Video card:  ATI Radeon 9550 SE
Monitor:  Xplio, 1440x900 LCD panel

I don't know why it worked, but it did so I'm not arguing.

---

