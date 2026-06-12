---
title: "Mic/Headphone Jack not working"
date: 2014-06-07
forum: Multimedia Software
---

### Post by gooeysan on 2014-06-07
I recently installed Ubuntu 14.04 on my Asus K56CB. It has the combined audio jack (like phones do). When i plug my speakers or  headphones in, I receive no output whatsoever. Ubuntu recognizes that i plugged something in since it mutes the internal speakers.
I've tried most of the things i could find on google.

---

### Post by Yellow Pasque on 2014-06-07
This person had the issue when rebooting from Windows: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1247480](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1247480)
Have you tried headphones booting straight into Ubuntu after power on?

Otherwise, try latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
If it doesn't work after rebooting, file bug:
```
ubuntu-bug audio
```

---

### Post by gooeysan on 2014-06-08
Thank you! I somehow didn't think to just easily try to update the driver.

---

