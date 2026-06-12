---
title: "Volume muted on startup"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by Whilt on 2006-12-05
Hi,

I'm new to Ubuntu, and am currently trying to deal with some of the minor problems that I've experienced since replacing windows with it on my laptop.  Main issue I'm having right now is that when I reboot the computer, the volume level is either muted or so low as to be inaudible.  However, the moment I adjust the volume control slider gotten by clicking on the speaker icon in the top-right corner (what's the term for this area, by the way?) either up or down, the sound level becomes audible until next boot.

I tried following the directions in the comprehensive sound problems solution guide to no avail.  Specifically, the first time I tried the command:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

it killed my gui, and I ended up reinstalling Ubuntu from scratch to get it working again.  Next, I tried

sudo alsactl store 0

after getting my volume to an appropriate level, but again I couldn't hear anything until I moved the volume slider.

Technical specs on my computer: I'm running Ubuntu 6.10 installed from the alternative install CD (my computer was too slow to handle the graphical installer.)  I'm running on an old Gateway 1450 Solo laptop, using what I believe to be some sort of crappy on-board sound.

Thanks!

---

### Post by Whilt on 2006-12-12
Just thought I'd also add that when I get multiple messages in rapid succession in gaim, sometimes the sound will begin playing at a higher frequency than normal for a while afterward.

---

### Post by motoperpetuo on 2007-09-20
I have the same problem with my Gateway Solo 1450. I also have to adjust the volume to get sound to start.

---

