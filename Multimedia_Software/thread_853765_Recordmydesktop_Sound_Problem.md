---
title: "Recordmydesktop Sound Problem"
date: 2008-07-08
forum: Multimedia Software
---

### Post by Metaleks on 2008-07-08
Hiya. My problem is the exact same one that was addressed in [this post]("http://ubuntuforums.org/showpost.php?p=5135536&postcount=12"). You'll notice that a fix has been suggested, and confirmed that it's working.

However, I still have the problem. My */etc/modprobe.d/alsa-base* looks something like this (the options portion):
```
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel position_fix=1
```
The fix is supposed to be the line:
```
options snd-hda-intel position_fix=1
```
I think I may have entered the fix incorrectly. The instructions were "add position_fix=1 to options snd-hda-intel in /etc/modprobe.d/alsa-base" Note that *options snd-hda-intel* didn't exist before this fix. Any help would be greatly appreciated. :)

---

### Post by Metaleks on 2008-07-09
Bump!

---

### Post by Metaleks on 2008-07-10
Bump!

---

### Post by Metaleks on 2008-07-12
Bumpitty bump.

---

### Post by Metaleks on 2008-07-14
Bump!

---

