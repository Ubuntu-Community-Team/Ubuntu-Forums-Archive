---
title: "lost sound after the last update"
date: 2010-06-21
forum: Multimedia Software
---

### Post by Benifited on 2010-06-21
after the most recent update i lost all system sound. i dont really know where to start tryn to fix this. any ideas?

---

### Post by Benifited on 2010-06-21
any help at all would be great

---

### Post by CajunPirate on 2010-06-21
I had the same problem today. I ran through this list and all is well after a reboot.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Hope it works for you as well,
Cheers!

---

### Post by Rickles65 on 2010-06-22
```
sudo apt-get remove --purge alsa-base

sudo apt-get remove --purge pulseaudio

sudo apt-get clean && sudo apt-get autoremove

sudo apt-get install alsa-base

sudo apt-get install pulseaudio
```

Works for me fine, BUT when I shutdown and turn it on later I have to do it all over again.

This is a REALLY annoying bug. We were set to field 5 desktops running 10.04 Desktop but not with a bug like this.

I've found no permanent solution yet anywhere.

---

