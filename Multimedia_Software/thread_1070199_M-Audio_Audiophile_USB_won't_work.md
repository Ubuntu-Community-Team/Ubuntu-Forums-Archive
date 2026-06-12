---
title: "M-Audio Audiophile USB won't work"
date: 2009-02-14
forum: Multimedia Software
---

### Post by spasticteapot on 2009-02-14
After I plugged in my M-Audio soundcard, no output came through it. I tried disabling onboard audio, updating the firmware ([http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)), and still nothing. 

While aplay -l lists three output devices for the card (presumably for line, S/PDIF, and headphone outputs), I get the following error message when I run alsamixer: 
alsamixer: function snd_ctl_open failed for default: No such file or directory


While I don't have pulseaudio, I do have libpulseaudio0 installed - I've heard it can cause problems. 
Thanks!

---

### Post by spasticteapot on 2009-02-18
Nobody?

---

