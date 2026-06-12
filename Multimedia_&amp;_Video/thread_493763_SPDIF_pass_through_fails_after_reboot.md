---
title: "SPDIF pass through fails after reboot"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by freestyla on 2007-07-06
Hey,

I've successfully got everything working for a HTPC...video out using the ati drivers, dvds playing, and spdif pass through...

all works well on a fresh install with iec958 unmuted and mplayer configured to pass through to spdif.  All 5.1 channels light up on the receiver and both dolby and dts are properly decoded by my receiver.  

Then I reboot.....

... and the ubuntu startup sound gets played through the receiver as PCM (PCM lights up on the receiver).  Now when trying to play DVDs configured to pass through to spdif, no more ac3/dts stream appears according to my receiver.  The spdif output still works as the OS can send sound to it (PCM), and i can play DVDs in stereo (PCM), but no ac3/dts stream works.

It is though a configuration setting has been changed just before or after reboot which enables the OS To use the spdif PCM which then doesnt allow pass through to work.  I'm not using any .asourdrc, just the OS defaults from a fresh install.  I've fresh installed 3x with the same results, and no amount of rebooting seems to fix the problem.  spdif is still visible in aplay -L

Can anybody shed any light on this?

Cheers

---

