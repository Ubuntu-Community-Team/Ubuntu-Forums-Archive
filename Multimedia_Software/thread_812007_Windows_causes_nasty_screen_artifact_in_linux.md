---
title: "Windows causes nasty screen artifact in linux"
date: 2008-05-29
forum: Multimedia Software
---

### Post by laizer on 2008-05-29
I've been running Ubuntu Edgy for a couple years now - generally happy.

Dell Inspiron 6400/e1505, Intel 945GM graphics chipset, Intel i810 driver

I have a Windows installation that I use periodically when I can't do it in linux. Yesterday, I was trying to get a wiimote whiteboard working in Windows.  In the process, I was driving an external projector out of windows. (and playing with bluetooth a lot, but that shouldn't matter.)

When I returned home to Ubuntu, I had screen artifacts that won't go away.  On the rightmost 20% of the screen, there are vertical lines, as if the last pixels in the picture where just dragged out.  The regular kicker bar is off the bottom of the visible screen.

Nothing I do gets rid of it.  I've reconfigured X, dropped in a known working xorg.conf, swithched between KDE and Gnome, switched between stretched and unstretched video modes in BIOS, gone back to windows and changed video modes.  It always returns.  I also tried setting the video mode with 915resolution, but to no avail.  It doesn't appear to do anything at all.

Some interesting behaviors:  The GDM login window doesn't have the artifacts.  Right after login, I see the mouse jump 100 pixels to the left, and the artifacts set in.

When I reconfigure X, the search for screen resolution clears away the artifacts.  The screen resets to an unnatural resolution, but the artifacts are cleared by that process.  The artifacts return on the next restart of X.

Any help is appreciated.  I'm at a loss on this one.

---

### Post by laizer on 2008-05-30
Figured it out.

With the projector plugged in to the laptop, *even though it was turned off*, the on-screen resolution of the laptop was messed up.  Just the presence of the plug through X for a loop.

My xorg.conf only listed one display, that's probably part of the equation.

Unplug the projector, problem goes away.

---

