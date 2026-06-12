---
title: "Finally got sound working...is there a 'better' way?"
date: 2008-12-14
forum: Multimedia Software
---

### Post by DefineByte on 2008-12-14
I bought a knew USB DAC to use with a box running Ubuntu - without X - and after a few struggles I've managed to get sound working.

The on-board soundcard (since disabled in the BIOS) worked fine so I knew ALSA was working but I just couldn't get any output with the DAC. It was being detected ('aplay -l' showed it) but mpd produced no output.

While rooting through all the configuration files I could find I noticed in '/etc/modprobe.d/alsa-base' the line 'options snd-usb-audio index=-2'. I commented this out and I now have working sound (albeit alsamixer doesn't seem to work but I'm not sure it's needed).

The question is, what is this line for and will commenting it out cause any problems? What's wrong with a USB soundcard being index 0? Is there a more correct way of fixing things? Will this cause problems in the unlikely event that I enable on-board sound again? Why can't I just accept that things now work and leave well alone? :D

Thanks all.

---

