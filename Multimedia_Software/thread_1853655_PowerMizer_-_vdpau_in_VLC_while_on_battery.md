---
title: "PowerMizer - vdpau in VLC while on battery"
date: 2011-10-02
forum: Multimedia Software
---

### Post by pjman on 2011-10-02
nVidia's PowerMizer is preventing me from viewing smooth HD video playback while unplugged from AC on my laptop (vdpau/VLC). While connected to AC, videos play fine.

nvidia-settings shows PowerMizer has the following Performance Levels:

PL | Graphics Clock | Memory Clock | Processor Clock

0 - 50 MHz - 135 MHz - 101 MHz
1 - 202 MHz - 324 MHz - 405 MHz
2 - 675 MHz - 1250 MHz - 1350 MHz


When I'm connected to AC power and view an HD video, PowerMizer shows that Performance Level 2 is used. When on battery only 0 & 1 are used. Unfortunately PL 1 isn't fast enough to view HD. How can I force PowerMizer to be allowed to use PL 2 while on battery?

---

### Post by WasMeHere on 2011-10-03
Try to select 'prefer-max-performance' according to the attachment!
It works for me.

If still no luck, try to change some energy saving setting (maybe in 'systems -- settings' menu or in the bios menu).

---

### Post by pjman on 2011-10-03
When I choose prefer-max-performance on battery it works but only goes up to performance level 1 - which isn't fast enough to get smooth vdpau playback. I've gone through the other power settings with no luck.

Is there any way to force the driver to use performance level 2 on battery when prefer-max-performance is set?

---

### Post by WasMeHere on 2011-10-04
It's stupid to set such rules, because nobody has enough fantasy to make it work for all situations.

I don't know where to tweak it, let us hope that someone who knows **how to make the GPU stay in Performance Level 2 on battery** reads this thread and helps you. At least it should be possible to let the system pretend that it is connected to the AC power, but you would need to do some programming.

Or maybe you post a new thread with that title ;-)

Good luck
Olle

---

