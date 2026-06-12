---
title: "NVidia Twinview: Maximize across just one monitor?"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by keflavich on 2007-09-30
The title probably says it all.

I'm using nvidia's twinview for my dual monitor setup with NVIDIA driver version 1.0-9755.  I've been using it for a few weeks, but yesterday I suffered a hibernate-related crash and ended up reinstalling big portions of the OS.  Previously, twinview worked mostly as expected: maximizing a window would maximize it in one window, and the bottom/top of screen bar would restrict itself to one window.

Now, maximizing spreads across two windows, which is extremely bad because my laptop monitor is 1280x800 and my external is 1280x1024 (obviously I can change the resolutions, but the scales will never match).  That means I lose significant portions of any maximize window.  Also, the lower panel spans both screens, which means that half of it is totally unaccessible.

I've read ~10 threads on ubuntuforums and another 5 on linuxquestions.org where people reported this problem, but I haven't seen any solutions.  The closest I've seen to an answer was [http://ubuntuforums.org/showthread.php?t=519096](http://ubuntuforums.org/showthread.php?t=519096), but the solution they showed (which was just an xorg.conf file I had to interpolate to my own) had no effect.  I don't think the problem is in xorg.conf because nvidia-settings seems to mostly ignore it, and I know I didn't make any modifications to xorg.conf with my previous setup that functioned as expected.

I've tried enabling Xinerama, which was another suggestion I found somewhere, and that has just disabled nvidia-settings with the error "The XRandR X extension was not found", and xrandr gives a segfault if I try to run it in a terminal.

I don't know what could have changed between my previous install and the reinstall.  Both are on the latest version of Feisty with the 2.6.20-16-386 kernel.

Thanks for the help,
Adam

---

### Post by keflavich on 2007-10-02
I've tinkered some more and discovered a few solutions.  First, I switched to Xinerama; this works but it's not dynamic.  So I went back.

Somehow after changing to Xinerama and then going back to twinview, things maximized correctly to just one screen.  I discovered one issue was that I was running nvidia-settings without preceding it with gksudo, and it did not default to asking for sudo access.  This meant that I could not save my xorg.conf changes.

Still, everything was not back to normal - the gnome-panel was on the wrong screen, so because my laptop/external setup is a 2560x1024 metamode with dead space, I still had some inaccessible real estate.

When I changed to 2560x800 and then changed back, though, it repaired things to be the way I expected.  Apparently the screen configuration is very sensitive to changes of resolution.

Adam

---

