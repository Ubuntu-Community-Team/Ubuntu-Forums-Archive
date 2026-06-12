---
title: "Pulse audio profile not retained"
date: 2014-05-26
forum: Multimedia Software
---

### Post by j-dowsett on 2014-05-26
I'm running Ubuntu Gnome 14.04, and have installed pavucontrol.  I have integrated 7.1 sound, this is the only audio device.
In a pavucontrol, under the Configuration tab, I need to deselect 'Analog Surround 7.1 Output + Analgo Stereo Input' (ie select something else) and then reselect it in order to get the sound to function correctly.

However - I have to do this every time a new audio stream begins, eg upon a new track beginning in a media player or a watching a new video ont he internet.

The correct profile remains listed in the dropdown box in pavucontrol, but it reverts to standard stereo output until I deselect and reselect the 7.1 option.  I recall having the same issue with Ubuntu 12.04, and I believe I resorted to removing Pulse and using Alsa, but I'd be grateful for pointers about how to fix it without doing that.

Cheers
Joe

---

### Post by ronb19495 on 2014-05-26
try this fix by odur
1. Uninstalling pulseaudio and purged it (sudo apt-get autoremove --purge pulseaudio).
2. Rebooted and removed ~/.config/pulse/ (rm -r ~/.config/pulse/)
3. Rebooted again and installed pulseaudio again (sudo apt-get install pulseaudio paprefs pulseaudio-esound-compat).
and also make sure 14.04 is fully updated

---

### Post by j-dowsett on 2014-05-27
Thanks, but sadly this has had no effect, the same behaviour remains.

---

