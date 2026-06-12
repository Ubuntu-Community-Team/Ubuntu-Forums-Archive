---
title: "No DVD playback"
date: 2008-07-19
forum: Multimedia Software
---

### Post by SouthernPott on 2008-07-19
I have been trying to set up VLC as the default DVD player following the instructions from the sticky at the top.  When I put a DVD in the drive VLC opens a small box then grays out after 20-30 seconds without the DVD ever starting.  

This is a used computer that I rebuilt for my neighbors children.  The one unanswered question is whether the DVD player worked before we put Ubuntu on it.  Previous owner had Fedora and I didn't bother to test the DVD playback.  I am able to get it to play CDs on the same optical drive.

I tried Totem and mplayer also.  What do I need to do in terminal to see the errors?  I read something about it earlier in this forum but didn't save it.

I was able to check the region settings with a DVD installed and they were correct.

Thank you.

---

### Post by SouthernPott on 2008-07-19
Nevermind.  I did the following and now it seems to work just fine.


sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

sudo /usr/share/doc/libdvdread3/install-css.sh


I already set VLC to be the default player and run in full screen mode.  Inserted a DVD, VLC started up and played the DVD.

---

