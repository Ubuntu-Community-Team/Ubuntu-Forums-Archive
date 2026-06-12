---
title: "Dual monitor in Gutsy"
date: 2007-12-18
forum: Multimedia &amp; Video
---

### Post by itFinallyWorks on 2007-12-18
Hello,
  I seem to be having difficulties getting my dual monitor working again in gutsy.  I had it working is Feisty (mergedFB), but I can't quite seem to get the last step working in Gutsy.

  The computer is a Toshiba A75-S211 laptop, the video card is a Radeon 9000 IGP (similar to the Radeon 9100 IGP), and the monitor is a Lenovo L192 widescreen LCD monitor.

  Ok, so here's what does work.  xrandr finds the monitor and sets the resolution correctly.  It doesn't start in the right position (it starts overlapped with the laptop screen).  The command  xrandr --output VGA-0 --above LVDS fixes that and puts the monitor by itself so it works like it should (in case you are wondering, it has to be above because there appears to be a limitation in the driver about the width - putting them next to each other makes it too wide, and yes I did tweak the Virtual parameters).

  So here's the problem.  I think the resolution is right on the external monitor, but something else is crazy.  The monitor shows the desktop/applications properly, but it doesn't spread across the monitor like it should.  Instead it is squished horizontally and offset part way across the monitor.

  Anybody know what the problem might be and how to fix it?


Thanks

---

### Post by itFinallyWorks on 2007-12-19
I figured out my own solution (no help from anybody here).  Here's what I did
On the desktop, I made a script.  The contents of the script are

#!/bin/sh
xrandr --newmode twoScreen 136.49  1440 1536 1688 1936  900 901 904 940  +HSync -Vsync
xrandr --addmode VGA-0 twoScreen
xrandr --output VGA-0 --mode twoScreen
xrandr --output VGA-0 --above LVDS

I could have adapted the for the xorg.conf file, but I hate messing with that thing (I find it confusing).

On another note, this is my second thread on ubuntu forums.  Both were issues with dual monitors.  I have had 0 responses.  I am not finding this support to be very supportive.  I love ubuntu otherwise though (I am a recent windows convert).

---

