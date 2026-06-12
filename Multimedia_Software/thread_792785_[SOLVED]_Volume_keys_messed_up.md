---
title: "[SOLVED] Volume keys messed up"
date: 2008-05-13
forum: Multimedia Software
---

### Post by Stunts on 2008-05-13
Hi all!
I've got this really strange problem, that you will probably laugh at, because it's kind of silly.
I've been having some problems configuring Pulse audio to work with ALSA applications (SDL games in fact) and I have messed a lot around the settings, followed "HowTo's", etc.
Bottom line is that in all this tinkering, my volume control keyboard shortcuts, all of a sudden started acting funny.
When I press "Fn + Vol up" or "Fn + Vol down" instead of controlling my output volume, Ubuntu is controlling the volume of the input device (my built in mic, or line in, or CD, or whatever is selected as default input in volume control).
Just to make things worse, this is the only way I have to quickly control the volume, since I'm running a laptop and it has no other sort of volume control.
I've tried to use the "System>Preferences>Keyboard Shortcuts", but to no avail.
The mute key is also attached to the mic rather than the speakers...

Anyone got any ideas?
Thanks in advance.

---

### Post by hermes0710 on 2008-05-13
Go to System>Preferences>Sound and in the first tab, at the bottom part there is a list, make sure you select there the device that you want the shortcuts to control (ex.PCM or Master)

---

### Post by Stunts on 2008-05-13
Yay!
It worked!!
Thank you so much!
I'll mark the thread solved.
I never tought it would be so fast!!

---

### Post by hermes0710 on 2008-05-13
Glad i helped :)

---

