---
title: "[SOLVED] Hotswap default sound device?"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Zorael on 2008-04-28
Is there any way to "hotswap" the default sound device in KDE?

I have a laptop with an integrated sound chipset, as well as an external usb sound device that I connect every now and then. The default device is the laptop chipset (snd-hda-intel), likely defined somewhere deep in /etc. Now, if I connect the usb device and I want Amarok to play through it, I have to go into Configurations, then Engine and enter 'hw:1,0' instead of 'default' in the stereo device field. And vice versa to restore.

So, can 'default' be redirected without restarting ALSA? I imagined there'd be an easy dropdown list in kmix to assign it to a device, but no.

Any ideas? Would appreciate it.

---

### Post by carpediem1337 on 2008-04-29
I was also wondering this.  I switch from my Sound card to my onboard sound all the time in Vista.

---

### Post by Zorael on 2008-04-29
Well, uh, this became very easy once I installed Pulseaudio.

---

