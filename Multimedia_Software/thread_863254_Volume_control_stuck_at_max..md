---
title: "Volume control stuck at max."
date: 2008-07-18
forum: Multimedia Software
---

### Post by illnin0 on 2008-07-18
Hi
I just installed the Ubuntu distribution on my laptop so forgive me if this is trivial stuff.

Everything seems to be working pretty ok except for my soundcard.

I do have sound but it appears like the volume won't be controlled. Whenever I try to drag the slider down from "Max" it jumps right back up when i release the mouse button. The sound is awfully loud and there's no way for me to control it since the speakers are built-in.

Hope someone can help me solve this issue...

---

### Post by tuxxy on 2008-07-18
Are you using alsaamixer?

---

### Post by illnin0 on 2008-07-18
> **tuxxy said:**
> Are you using alsaamixer?

I didn't know about that...

"sudo apt-get install alsamixer" gives a "couldn't find package" though :confused:

---

### Post by PaulOfCongleton on 2008-07-19
Hello all,

We have the same problem with our Dell Inspiron 1525 laptop, running 7.10, which we bought pre-installed from Dell. It used to work fine, but became stuck a few weeks ago.

We are already using alsamixer.

I've got a bit more detail on the symptoms, which might be useful...
The same problem occurs whether I use the buttons on the keyboard, or left-click the sound icon on the upper-right panel.
We discovered a sort of workaround, whereby if you press the 'mute' button, you can then turn the volume down. If you then un-mute it, the volume stays where you left it. After this, if you press the 'down' button, the volume goes *up*, ending up at its previously stuck position.
Another thing we discovered is that if you right-click the sound icon and select 'Open Volume Control' (bringing up the two-channel mixer), the left hand channel will adjust quite happily, while the right-hand channel is in the stuck state.
I did wonder whether this could be some sort of permissions issue...?

I've noticed a couple of other threads which seem to deal with the same, or similar, issues:

[http://ubuntuforums.org/showthread.php?t=851017](http://ubuntuforums.org/showthread.php?t=851017)

[http://ubuntuforums.org/showthread.php?t=829787](http://ubuntuforums.org/showthread.php?t=829787)

All the best,

Paul.

---

