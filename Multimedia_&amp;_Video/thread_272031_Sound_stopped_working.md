---
title: "Sound stopped working"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by avicado on 2006-10-05
Hello.  I've had Ubuntu installed on my laptop (HP Pavilion zt1000) for a while with no problems.  All of a sudden, my sound stopped working.  I know it's not a hardware problem, as when I boot into WinXP, it works just fine.  Plus, the sound works up until I login to my account -- it plays a sound showing my login was successful, and then it stops working.  When I try to open the volume control, I get an error dialog box that says, "No volume control GStreamer plugins and/or devices found."

`aplay -l` resulted in the 'no sound cards found' error.

lspci -v shows my sound card:
Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller

I tried the `sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils` trick, then reinstalled them -- still no luck.

I'm not sure what I should do at this point.  The General FAQ seemed to say I should look up the ALSA driver, but it doesn't say I have to download it, just to make sure it exists (which I believe it does).  Can anyone help?

Thanks!

---

