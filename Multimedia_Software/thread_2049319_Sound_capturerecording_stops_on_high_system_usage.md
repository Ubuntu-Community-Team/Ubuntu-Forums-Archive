---
title: "Sound capture/recording stops on high system usage"
date: 2012-08-28
forum: Multimedia Software
---

### Post by filu on 2012-08-28
(sorry I've already posted it at the beginners' talk but no reply there)

I'm running Ubuntu 12.04.1.

System records (captures?) sound from the external microphone normally (checked with arecord). However, when I start any 'heavier' app (like firefox) it stops recording (arecord simply hangs). This is especially annoying while skyping as I can't do anything during the talk and sometimes the capturing stops even without any action during skyping (suddenly the person stops hearing me).

In case if this happenes I close skype (otherwise it hangs upon the next step), type "sudo alsa force-reload" and the capturing (recording?) works again until the same thing happens.

The problem occured on my computer since the first ubuntu installation: with 10.04, then after its reinstallation and again after the upgrade to 12.04.1 (no problems with win XP before).

---

