---
title: "Flash 100% CPU usage."
date: 2010-01-21
forum: Multimedia Software
---

### Post by NiGhtMarEs0nWax on 2010-01-21
Hi, it seems recently that flash video is starting to use a ridiculous amount of cpu. when I was on windows XP 1080 videos decoded perfectly, worked fine, even when I first switched to ubuntu a few months back there was no problems as far as I could see. only in the last week I have noticed problems with flash when in fullscreen mode for all resolutions, obviously the higher the resolution the greater the problem. 

im using the most recent beta build of adobe flash player, I upgraded from the most recent stable build because I heard it helped; but it hasn't made a difference.
HD video playback (non-flash) is fine, I have some 1080 videos on my hard drive that work flawlessly, it seems either firefox or flash itself is sucking to a point of being unusable.

Has anyone else noticed this problem?

I'm running Karmic with Firefox 3.5.7, flash 10.1.52 beta (i think). i'm also using the most recent xorg ati drivers from the repositories.


Does anyone have a fix for this?

---

### Post by lovinglinux on 2010-01-21
Your description of the problem is similar to mine, included in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). There are few Flash tweaks there, but nothing miracle. The only real way I could find to "fix" this was to upgrade the CPU from a single core P4 to a Core2 Duo. Flash still uses too much CPU, but now it plays smoothly and without lagging the machine.

---

