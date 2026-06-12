---
title: "Edirol UA-1000 sound card Help please."
date: 2012-05-31
forum: Multimedia Software
---

### Post by eddie3000 on 2012-05-31
I have read that the UA-1000 usb 2.0 sound card works under linux. I haven't found much on this forum, and googling around I have found some information that's useless to me because I don't understand it. :confused: 
At the moment I am using ubuntu 12.04. Could somebody help me please in finding information to get it going? Thanks.

---

### Post by anderst on 2012-10-22
Hey, my ua-1000 is also not recognized as an audio interface in Ubuntu 12.04.

My syslog says:
```
Oct 22 17:35:35 atc-laptop pulseaudio[1827]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-EDIROL_UA-1000_ZR41043-02-UA1000" card_name="alsa_card.usb-EDIROL_UA-1000_ZR41043-02-UA1000" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Oct 22 17:35:36 atc-laptop pulseaudio[1827]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
```

Anyone?

---

