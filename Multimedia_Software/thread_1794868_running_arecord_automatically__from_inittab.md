---
title: "running arecord automatically  from inittab"
date: 2011-07-01
forum: Multimedia Software
---

### Post by stickjam on 2011-07-01
I'd like to set up a process to automatically run *arecord* whenever DSR is asserted on tty1 and stop when DSR drops. I have a DC power supply wired up to an RS-232 DB9 connector to simulate a terminal being present whenever the PA system I'm recording from is powered on.
 
My first instinct is to replace the /sbin/getty in inittab with another process (shell script) yet to be written. 
 
Any ideas how you'd approach this? My background ranges from audio production, hardware design, to software development including Unix flavors. So any level of geekiness is welcome in your suggestions. 
 
One obstacle I've run into before is that the drivers for my audio interface (Lexicon Alpha) don't seem to be available unless the console is logged in. I've got it running now on Karmic Koala using crontab and the console locked. But the desire is to always record anytime the PA is turned on.  I'd rather not need to have the console logged in.  Maybe that limitation is gone in Natty, which I'm moving to now???
 
Thanks!
 
-Bob

---

