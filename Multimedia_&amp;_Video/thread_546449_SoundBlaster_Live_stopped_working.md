---
title: "SoundBlaster Live stopped working"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by foo Utu on 2007-09-08
it was working fine, but now my SB Live Value (emu10k1) won't load. my onboard sound continues to work. also i found it impossible to set a default sound card on subsequent reboots the order was always lost.

lspci reports "02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)"

but when i 'sudo modprobe snd-emu10k1' the card does not appear when i 'cat /proc/asound/cards' or 'cat /proc/asound/modules'

any ideas?

---

### Post by linuxwizard on 2007-09-08
With the recent updates seen some different issues sound is one of them. Might look at Launchpad and see if a bug has been reported could be a work around or fix.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20)

---

