---
title: "[SOLVED] How can I disable pulseaudio through the terminal?"
date: 2008-07-07
forum: Multimedia Software
---

### Post by csc2ya on 2008-07-07
I've got a problem regarding pulseaudio on hardy heron. I've noticed that flash videos (mainly youtube) would play for a few seconds, then stop.

I've now narrowed it down to a problem with pulseaudio, as if I go into system tools > system monitor, and end pulseaudio through there, flash video's then play with no problems.

I've tried going into synaptic, and removing pulseaudio, but that also wants to remove gnome at the same time, which i'm using, so I can't remove it.

I also cannot get into the system menu on the panel menu (It freezes xserver whenever I try. This occurred after installing the mac4linux pack), and so I can't even just change whether pulseaudio is enabled or not.

Is there any way to disable it through the terminal, as this currently seems the only possible way of sorting it out.

---

### Post by wolfen69 on 2008-07-07
from [here]("https://wiki.ubuntu.com/PulseAudio") :
PulseAudio Removal

If you decide you no longer like PulseAudio and would like to disable it: Remove the added lines to /etc/asound.conf If /etc/asound.conf did not exist when you installed PulseAudio, you may remove /etc/asound.conf entirely. 

After this, you may remove all of the installed PulseAudio packages. 

To disable pulseaudio in hardy you need to select alsa for for all options in /system/preferences/sound

---

### Post by csc2ya on 2008-07-07
Thanks for the reply. However, there doesn't seem to be an asound directory in /etc for some reason (I did select to show hidden directories).

I'm unable to change it through preferences either due to gnome freezing whenever I go to open the system menu.

I've noticed some other things in that wiki entry that may fix it though. I'll give those a try later on.

---

### Post by csc2ya on 2008-07-08
I noticed on that wiki entry, that one of the things suggested was to downgrade the libflash plugin. I've done that, and flash video's now work again.

---

