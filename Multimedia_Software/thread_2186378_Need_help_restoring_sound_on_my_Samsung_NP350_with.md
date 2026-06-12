---
title: "Need help restoring sound on my Samsung NP350 with Ubuntu 12.04 64bit"
date: 2013-11-07
forum: Multimedia Software
---

### Post by lucacerone on 2013-11-07
Hi everybody,
I made some mess with the packages on my laptop (a Samsung NP350) with Ubuntu 12.04 64bit (fully updated),
and as a consequence the sound no longer works (I tried to install Cinnamon, but didn't like it and when I removed it
some packages where deleted including pulseaudio and some sound related ones; now I stick with Gnome Fallback).

I have tried to follow the steps in the sticky post, but they didn't help me (and seem a bit outdated).

In my sound settings I can see a device called Dummy Output, no input device and hardware detected (before I messed with my computer
the card was correctly detected and everything worked just fine).

I have no idea how to detect and solve the issue.

Removing the .pulse directory didn't help, nor issuing ```
pulseaudio -k
```.
Actually with ```
pulseaudio -k
``` sometimes I don't receive any message, other times I get an error message:
> E: [pulseaudio] main.c: Failed to kill daemon: No such process

Any help in finding the problem and possibly solving it would be really appreciated.
Thanks in advance for all the effort!

Cheers,
Luca

---

### Post by lucacerone on 2013-11-07
*bump*

---

### Post by lucacerone on 2013-11-07
apparently I restored the sound following the guide here: [http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)
although the sound indicator still shows no sound-card.

---

