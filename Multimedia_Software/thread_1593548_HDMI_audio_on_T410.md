---
title: "HDMI audio on T410"
date: 2010-10-11
forum: Multimedia Software
---

### Post by zerocon on 2010-10-11
Hi!

After a clean install of 10.10 on my ThinkPad T410 I found audio over the DisplayPort/HDMI no longer worked.

I did install linux-alsa-driver-modules-2.6.x and this has resolved the issue somewhat.

aplay -l lists 5 devices:
card 0, device 0 - internal audio
card 1, device 3
card 1, device 7
card 1, device 8
card 1, device 9

I unmuted all 4 devices off card 1 (nVidia HDMI) in alsamixer and still no result when switching between output devices in gnome's sound manager.

I found that card 1, device 7 actually works, where it's now probably trying to go to card 1, device 3.

My question is how to configure my device so gnome sound manager will use 1,7 by default, rather than having to specify this at the application level.

Any ideas? Thanks!

---

