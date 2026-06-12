---
title: "[SOLVED] Attempted to install pinnicle dazzle dvc170, now my webcam does not work."
date: 2008-08-21
forum: Multimedia Software
---

### Post by waka324 on 2008-08-21
I tried to install a usb capture device, the Dazzle 170, but it failed, and I can't use my webcam now. I would appreciate any help that could be given. I am using 64 Bit Hardy.

---

### Post by Crafty Kisses on 2008-08-25
Uninstall any drivers you installed and software for the Dazzle device, this happened to me too because I have the same capture card, so what you want to do is remove all folders and drivers and software associated with Pinnacle after that try this:

Open Ekiga and see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly. If that doesn't work post results of > lsusb

---

### Post by waka324 on 2008-08-25
unfortunatly, I had no Idea of what drivers I had installed, I followed several tutorials for different capture devices hoping it would work for mine, so I decided to reinstall. Oh well. I guess I leared a valuble lesson in creating a backup of the system before editing. Thanks for the reply.

---

