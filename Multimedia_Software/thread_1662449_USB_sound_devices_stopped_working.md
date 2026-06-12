---
title: "USB sound devices stopped working"
date: 2011-01-08
forum: Multimedia Software
---

### Post by tontaube on 2011-01-08
Hi,

Im running Ubuntu 10.10 and a couple of days ago, my usb sound deviced stopped working, possibly because of a recent update, as I didn't change something on my system as far as I can recall.
My internal sound card still works just fine whatsoever, but my external devices,

E-MU 0202 USB
Logitech USB Headset

which also used to work flawlessly in the past, don't play audio anymore.
Although they are still detected and selectable in the PulseAudio Volume Control. I can exclude hardware problems because everything is fine in WinXP. 

Please give me a little assistance in tracking down the issue.


Thanks in advance,
tontaube

---

### Post by kostkon on 2011-01-08
Try installing *gnome-alsamixer* and check the "hardware" volume levels and switches of your usb card.

---

### Post by tontaube on 2011-01-08
kostkon, thanks for the hint!

I was successful using a mixer called QAMix. Mysteriously both USB devices have been muted and the volumes have been at lowest level. This fact was not displayed in the PulseAudio GUI.

Anyway, unmuting and setting volume levels has enabled my audio again. Great.

---

