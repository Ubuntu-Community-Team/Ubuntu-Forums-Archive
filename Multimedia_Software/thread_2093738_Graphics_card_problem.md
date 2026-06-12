---
title: "Graphics card problem"
date: 2012-12-11
forum: Multimedia Software
---

### Post by iamtommo on 2012-12-11
Sorry if this is in the wrong section.

So basically, i recently upgraded from Radeon HD 5450 to the 6570, and when i boot into linux now, the login screen is purely green, i can still hear the sounds and i can login to be greeted by a total white screen after the login sounds finish. This is probably because i do not have the correct drivers but i'm not sure how i could install the drivers without a display.

Even though i cannot see anything, i can still login and open a terminal and probably execute some commands to install the correct drivers, with a bit of help?

Thanks.

---

### Post by QIII on 2012-12-11
Assuming you haven't updated your Ubuntu version as well, the first thing I would try is to initialize.

From GRUB, boot to the command line.

Execute

```
sudo aticonfig --initial
```

and reboot.

If that doesn't work, purge and reinstall the driver, initialize and reboot.

We'll help with that if it comes to it.

---

### Post by iamtommo on 2012-12-11
I just booted into the recovery console>root and reinstalled the driver + reset xserver settings, and it worked, but thanks anyway.

---

