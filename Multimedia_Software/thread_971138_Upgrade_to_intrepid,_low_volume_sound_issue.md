---
title: "Upgrade to intrepid, low volume sound issue"
date: 2008-11-04
forum: Multimedia Software
---

### Post by kev000 on 2008-11-04
This is kinda an odd issue.  I upgraded a slimmed version of Ubuntu from feisty to gutsy to hardy to intrepid.  This slimmed version runs matchbox-window-manager and a specialized touchscreen desktop (called nGhost: [http://wiki.openice.org/index.php/The_nGhost_Project](http://wiki.openice.org/index.php/The_nGhost_Project) ).

I can turn up the volume on every channel I can using alsamixer, but I still get very low volume level out of the right speaker channel and almost nothing out of the left speaker channel.

I know intrepid uses pulseaudio by default, but I should be able to use pure alsa like I did in previous versions.  Just to rule out pulseaudio, I installed it and it made no difference.

Relevant Hardware:
Via Epia M10000 
VIA VT1616 AC-97 Audio chip

other details are that i run X directly from runlevel 1.  I've tried loading other runlevels and that didn't make a difference.

I'm hoping that someone has an idea of a possible package i'm missing, or some debugging tip that will help me get sound back.

thanks

---

