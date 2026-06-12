---
title: "Only noise with analog HVR-1300"
date: 2012-03-25
forum: Mythbuntu
---

### Post by thorwil on 2012-03-25
Hello, even though all the kernel modules seem to be in place and a channel scan delivers results, I end up with noise on the screen when watching or recording any channel.

This is with Mythbuntu 11.10 64bit and a Hauppauge WinTV-HVR-1300, analog cable (Germany).

I doubt it's related, but when I turn on the HTPC, artefacts appear on the Display (Display and HTPC receive their signal from a splitter).

A ```
cat /dev/video0 > test
``` fails with Input/output error.

Any ideas?

---

### Post by thorwil on 2012-03-25
```
mplayer /dev/video1
``` in contrast kinda works. I once even managed to make out some content in the noise. Attempts to tune via ```
v4l-ctl -f
``` failed.

Mythtv's Watch TV shows just black for all channels.

---

