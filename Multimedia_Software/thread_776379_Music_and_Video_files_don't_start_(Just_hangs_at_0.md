---
title: "Music and Video files don't start (Just hangs at 0:00)"
date: 2008-04-30
forum: Multimedia Software
---

### Post by nystud162 on 2008-04-30
After Hardy Heron update:

Okay, this is weird. Occasionally when I try to play a video or audio file, it just hangs at 0:00 and doesn't play anything. But Youtube still works with sound and all. I can't figure out why.  And it's not like sound doesn't work, It would be working fine, then if I take a rest SOMETIMES when I come back it will do this.

MPlayer can play both video and audio files, but not Totem or Amarok.

---

### Post by nystud162 on 2008-04-30
Soooo, apparently It had something do do with the "pulse-audio" process?
I killed it in the System Monitor and then tried to play an audio file and it all works now... I've only done this once so I'm not sure this is what fixed it.  Next time it happens I'll do the same thing and see what happens.

---

### Post by inchaos on 2008-05-01
Thank you---I was having this exact problem.
Now, to disable pulseaudio on boot...

---

