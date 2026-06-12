---
title: "[SOLVED] Out of range error message"
date: 2008-07-25
forum: Multimedia Software
---

### Post by Benjaminp on 2008-07-25
I'm guessing that this is the right place to post in,; i think it might be a video card/screen resolution problem.

When I boot up my Ubuntu 8.04 computer, (when the Ubuntu loading screen comes up, with that orange progress bar), on the middle of the screen, theres a message saying "Out of Range". I thought that it might have something to do with my screen resoluction, but I tried switching it to all the different modes several times, but nothing happened to the out of range thing.
It disappears before the login screen pops up.

Any help would be appreciated. If you need any more information, please ask!

---

### Post by overdrank on 2008-07-25
> **Benjaminp said:**
> I'm guessing that this is the right place to post in,; i think it might be a video card/screen resolution problem.

When I boot up my Ubuntu 8.04 computer, (when the Ubuntu loading screen comes up, with that orange progress bar), on the middle of the screen, theres a message saying "Out of Range". I thought that it might have something to do with my screen resoluction, but I tried switching it to all the different modes several times, but nothing happened to the out of range thing.
It disappears before the login screen pops up.

Any help would be appreciated. If you need any more information, please ask!
Hi and what is the model of the graphics card?
Have you booted to recovery mode and tried the xfix option?
Recovery mode is usually the seconded choice from the grub.
Did your system use the live cd without issues?
You may also use the ctrl, alt, F1 keys while ubuntu is booting to see any errors.

---

### Post by Yellow Pasque on 2008-07-25
The splash screen is out of range? Try editing usplash.conf
```
gksudo gedit /etc/usplash.conf
```

Also, a little more info on your display and video card might be helpful if that's not what you were describing.

---

### Post by Benjaminp on 2008-07-25
My graphics card id a Nvidia GeForce 8600 model.
Yes, I've tried the recovery mode with the xfix option.
I tried the Shift Ctrl, Alt and F1 key when it was loading, and no messages came up... but the out of range thing is still there.

I just opened up my splash screen configuration file, and heres all the data that was in it:

xres=1280
yres=1024

should i try changing that to a lower resolution, or would that cause errors?

---

### Post by Yellow Pasque on 2008-07-25
Try 640x480, and if that doesn't work, change the boot option to nosplash in GRUB
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Benjaminp on 2008-07-25
I tried the 640*480 mode, and it seemed to work when it was shutting down, as no error message appeared.

However, when I started the computer, the screen resolution was back to the 1024 * 768 mode, with the out of range error message. 

I tried shutting it down again after that, and the error message disappeared (when it was turning off).
Is the startup resolution stored in a file separate from the shutdown resolution?



Oh OK I switched bootscreens and it seems to work! Thanks for your advice!

---

### Post by timominous on 2009-11-20
how did you change the bootscreens.?

---

