---
title: "Strange webcam image"
date: 2008-08-17
forum: Multimedia Software
---

### Post by QkEterror on 2008-08-17
The main problem here I think is that I have an old Philips 2U webcam (PCVC820K/00) which needs a jpeg compression module in the driver, that Linux doesn't support for obvious reasons (is not supposed to be in the kernel). However, I installed the ov51x driver from Rastageeks which does support the jpeg compression. 

This seems to work fine in vlc, but in the software where you actually use your webcam (ekiga, skype), it only shows a flashing coloured square (see attached image). After a lot of trying to make this webcam work I have the feeling I'm very close, so can somebody tell me how to make it work?

---

### Post by linuxwizard on 2008-08-17
In Ekiga did you work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

---

### Post by QkEterror on 2008-08-18
> **linuxwizard said:**
> In Ekiga did you work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

Thank you for the reaction. I already did what you suggested, but the ov51x driver doesn't support v4l2 yet, so it doesn't work. It completely turns of the webcam support of ekiga

---

