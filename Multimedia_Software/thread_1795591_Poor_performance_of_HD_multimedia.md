---
title: "Poor performance of HD multimedia"
date: 2011-07-02
forum: Multimedia Software
---

### Post by dtuza on 2011-07-02
Hi,

I've noticed that both VLC and Banshee are performing poorly when I try to play high-def video files - particularly speaking about matroska video files.

When I say performing poorly, it's a bit difficult for me to articulate exactly what's happening... it looks like the player is dropping a frame every couple of seconds, but running VLC -vvv doesn't log any frames being dropped.  I do get an occasional "late picture skipped" message (no more than one per 8-10 minutes), but not enough to explain why it seems like I'm probably getting a frame or two dropped every few seconds.  It could just as easily be that the frame rate's running slow, but I don't see how to view this in VLC.

I've followed the steps in the sticky on the front page of the multimedia & video forum through steps 1 and 2.  Steps 3, 4, and 5 didn't seem to contain any information relevant to the problem at hand or to Ubuntu 11.04.

If anyone has any thoughts on how I can address this, I'd appreciate it.  Happy to provide any info that would be required as regards my system.  For starters, the system's running Ubuntu ver. 11.04 on a Radeon HD 5450 video card.

Thanks in advance for any advice.

---

### Post by dtuza on 2011-07-04
Just wanted to post a follow-up to this, as I've been doing some tinkering to try to fix my original problem:

I've had some success disabling late frame dropping in VLC under:

Tools > Preferences > All > Video > Un-check "Drop late frames".  I also un-checked "Skip frames" under the same menu.

Everything's still a bit jerky and stutter-y, though... just minor enough to be irritating.  Any further suggestions would be appreciated.

---

