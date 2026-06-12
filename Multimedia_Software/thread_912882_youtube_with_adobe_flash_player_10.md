---
title: "youtube with adobe flash player 10"
date: 2008-09-07
forum: Multimedia Software
---

### Post by emco83 on 2008-09-07
has anyone noticed that when you watch youtube video on fullcreen is ok,but when you return it back in normal mode the screen freezes.when you click on screen twice the video continues.
the main problem for me is that when i try to watch in high quality it says WE'RE SORRY,THIS VIDEO IS NO LONGER AVAILABLE:confused:
with adobe flash player 9 the screen is choppy in fullscreen

---

### Post by emco83 on 2008-09-09
has anyone had this problem?
is there any fix for that,or some new version of adobe flash player?

---

### Post by Beretta_NZ on 2009-02-22
If you're able to watch Youtube clips at all in Ubuntu with any flash plugin, ANY screen size, then you are a very lucky person. For most people the Adobe plugin in Ubuntu causes massie CPU usage and the video freezes up every few seconds.

---

### Post by kiruch on 2009-02-22
LOL yes, you should be glad that you can watch youtube at all :)
for instance, my firefox freezes AFTER i watch something. and it doesnt' want to go fullscreen.

---

### Post by derway on 2009-02-23
No Problem here.

But it was hell getting swfdec to quit trying to play flash for me.  Could that be your problem?

I have a fresh install of 8.10, and at first I optimistically tried to use swfdec, but it will not play interactive flash games, and plays videos badly.

Using the "add remove applications" to remove stuff does not really remove it.  After installing the non-free flash, and removing swfdec, it still did not work right.

Close inspection of web pages with flash, revealed FF was still using swfdec.

I had to use synaptic package manager, to remove everything related to flash or swf, then search out and manually delete everything with swfdec in the name, and then reinstall the adobe version of flash player and now it is working great at both videos, (no freezes before or after full screen), and plays interactive flash games like a champ.

CPU usage was running at 12-15% of each ht processor during video playback.

HTHs,
Don

---

