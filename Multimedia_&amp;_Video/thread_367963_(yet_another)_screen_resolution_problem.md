---
title: "(yet another) screen resolution problem"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by Pikestaff on 2007-02-22
I know a lot of people have this problem and there are tons of threads about it but I'm not having any luck with the fixes suggested in those threads.  Basically I'm not getting any higher than a 1024x768 resolution, even though I got 1280x1024 in Windows.

I've reconfigured xorg, I've added "1280x1024" to the xorg.conf file, I've installed the right drivers (at least, I think I have) and I'm having no luck.  The closest I got was when I edited in the correct horiz/vert rates for my monitor, but when I rebooted it got me to the login screen (which appeared to be in 1280x1024, what I want) but wouldn't let me log in... when I tried, the screen turned black for a few seconds and then took me back to the login screen.  So I had to can that idea.

I'm using an NVIDIA GeForce 6800 XT graphics card and my monitor is a 19" HP L1906.  I'm running Kubuntu 6.06 Dapper.  Please, any help would be appreciated [-o< thank you!

---

### Post by MasterOfDisaster on 2007-02-22
In the terminal, type nvidia-settings, and try to set the resolution from there.

---

### Post by Pikestaff on 2007-02-23
Hmm, a box pops up with a few options in it, but screen resolution isn't one of those options...

---

### Post by Pikestaff on 2007-02-23
Okay, I have (mostly) fixed this problem!  Here's what I did in case anyone else has a similar problem with the same monitor/video card:

When reconfiguring xorg, one of the first things it asks is what kind of drivers you want to use... choose **nvidia**, not nv or vesa.  Then, later on, it asks you what kinds of screen resolutions you want to have... 1280x1024 is usually not selected by default.  So arrow down and find it (or whatever resolution you want), and then press the **spacebar** to select it (it took me a while to figure out that you have to press the spacebar.)

And that should be it!  Choose defaults for everything else and then after you reboot and log back in you should be able to choose the right resolution in System Configuration :KS  You might have to change some more settings after that (so it's set at 60Hz, for example) but it should work.

That said, I am having some problems with the mouse cursor "flickering" when I try to load things... I've tried messing with some of the settings but it's still flickering.  Any ideas on how to fix it?

---

