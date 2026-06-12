---
title: "Audio issues (playing mono instead of stereo)"
date: 2008-08-19
forum: Multimedia Software
---

### Post by DeeDubb on 2008-08-19
Most of my files are working fine, and I've got every codec I could find, but one of my mp4s is only playing in mono or just playing surround sound, I still can't figure it out. It's like the main dialog is muted and only various action noises are played. Anyone know of a codec that might square me away?

---

### Post by SGundamZro on 2008-09-11
I have a similar problem, except that it involves every audio and video I played.

Edit:  I found a possible solution in this thread: [http://ubuntuforums.org/showthread.php?t=853491&highlight=mono+stereo](http://ubuntuforums.org/showthread.php?t=853491&highlight=mono+stereo)

This is what I tried:  From terminal: alsamixer

After that a moxer should be displayed.  If it says off next to Item:Master, then press "M" and it should fox it, at least it worked for me.  Otherwise, I can;t help you that much since I'm still a newbie at using linux.

---

