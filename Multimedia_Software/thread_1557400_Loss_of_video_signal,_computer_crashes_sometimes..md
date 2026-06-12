---
title: "Loss of video signal, computer crashes sometimes."
date: 2010-08-20
forum: Multimedia Software
---

### Post by CesarRz on 2010-08-20
:mad:Hi, I just upgrade from 8.4 to 10.04 Ubuntu, my problem is that I lose the signal on my monitor, I took the monitor to have it check and it was okay, I was told that maybe my video driver for my new Ubuntu version could be the problem; How can I upgrade new video drivers to my system? If I change my video card, could that be of any help?
Any help out there would very much appreciated.
Thank you.

---

### Post by Naitsirhc Hsem on 2010-08-20
I would recommend looking in System > administration > hardware drivers

---

### Post by tommcd on 2010-08-20
What video card do you have?
Do you have a screen saver running? If so, then disable it and see if the problem goes away.

---

### Post by fillintheblanks on 2010-08-20
This happens to me sometimes when I have compiz turned on. I have nvidia proprietary driver. Turn off compiz and its ok.

---

### Post by CesarRz on 2010-08-24
> **fillintheblanks said:**
> This happens to me sometimes when I have compiz turned on. I have nvidia proprietary driver. Turn off compiz and its ok.

Thanks, I'll check my video card, I don't know what type is there now, but I'll open my computer and check all the fans as well as my psu.

---

### Post by tommcd on 2010-08-25
> **CesarRz said:**
> Thanks, I'll check my video card, I don't know what type is there now, but I'll open my computer and check all the fans as well as my psu.
To find out what video card you have, just run:
```
lspci | grep -i vga
```
Post the output here if you are unsure. 
If you have nvidia, you can go to: system > administration > hardware_drivers to enable the nvidia driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

