---
title: "No sound after Wine Install"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by tj111 on 2007-10-29
After installing Wine, I no longer have any sound on my computer.  When I run "winecfg" and click on Audio, I get this message in the terminal:
> 
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

I can't figure out which library its referring to, or how to fix this.  I've tried every combination of driver options available, none work.

---

### Post by cogadh on 2007-10-29
You can ignore the Jack message, unless you are using Jack as your Wine sound driver (most people should be using ALSA). What are your sound settings in Wine and what version of Wine are you using? Does the sound problem continue after a logout/login or reboot?

---

### Post by tj111 on 2007-10-29
I installed new versions of the ALSA and Jack libraries (after much googling).  For some reason had to run an fsck on reboot, but right now everything appears to be working :).  I'll run a game under Wine and see if that works too.  Funny as it is, if you didnt mention a reboot I'd probably still be messing with it.

---

