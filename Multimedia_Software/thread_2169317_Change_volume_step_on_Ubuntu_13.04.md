---
title: "Change volume step on Ubuntu 13.04"
date: 2013-08-21
forum: Multimedia Software
---

### Post by cserpell on 2013-08-21
Hi,

I updated from version 12.04 to 13.04, and now the previous solution I found searching internet doesn't work for me: The gconf volume_step doesn't exist anymore.

What I am trying to do is to know who handles the volume up/down key events, so I can change the current behavior. I noticed Xorg handles the events KEY_VOLUMEUP (115), KEY_VOLUMEDOWN (114) and then propragates them. So, my question would be like "Which program does handle volume control events from unity side?" I know there is a bug but I would like to know just that.

Is there a general way to know which program handle different Xorg, and all layers above, events?

---

### Post by Yellow Pasque on 2013-08-21
It used to be gnome-settings-daemon. I'm not sure if that's still the case.

---

### Post by cserpell on 2013-08-21
Then maybe it is now hardcoded [here]("https://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/media-keys/gsd-media-keys-manager.c?h=gnome-3-6#n101")?

---

### Post by Yellow Pasque on 2013-08-21
Okay, I found this bug. [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133)

The volume step is now hardcoded: [https://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/media-keys/gsd-media-keys-manager.c#n107](https://git.gnome.org/browse/gnome-settings-daemon/tree/plugins/media-keys/gsd-media-keys-manager.c#n107)

---

### Post by cserpell on 2013-08-21
Yes, that seems to be the case. FYI, this is a useful page in cases like this one: [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting) .

Leaving the volume control keys aside, how would you know a program that listens to a certain event?

---

