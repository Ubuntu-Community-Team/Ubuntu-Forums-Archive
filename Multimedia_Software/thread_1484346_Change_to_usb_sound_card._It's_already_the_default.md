---
title: "Change to usb sound card. It's already the default one, but output still internal."
date: 2010-05-15
forum: Multimedia Software
---

### Post by myjess on 2010-05-15
I have a USB sound dongle and have followed the instructions to put it as the default in alsa-base.conf.
I have also created /etc/asound.conf for pcm and ctl to hw 1, although I am about to put this to 0 and reboot.
I can change the output to USB in the sound preferences but this setting does not stick over reboots.

Help really appreciated.

Thanks.

---

### Post by myjess on 2010-05-16
bump.

Maybe the sound is controlled by pulseaudio so if you have any knowledge of that either, it may help.
Thanks.

---

### Post by myjess on 2010-05-16
Never mind. I just blacklisted the internal sound card.

---

