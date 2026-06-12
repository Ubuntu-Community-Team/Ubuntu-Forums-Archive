---
title: "Used Comp. Sound Guide but sound lost again after re-reboot"
date: 2009-09-04
forum: Multimedia Software
---

### Post by billynomates on 2009-09-04
I got to the stage in Comprehensive Sound Problem Solutions Guide where it says to purge a bunch of packages and then reinstall them:

> (1) Remove these packages
Code:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```


(2) Reinstall those same packages
Code:

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

...

(3) Reboot


After I reboot, everything works perfectly! But then if I reboot again, it stops working! I can reproduce this too. Any ideas?

---

### Post by billynomates on 2009-09-06
bump

---

