---
title: "Sound Skipping in Lucid on Youtube and Pandora"
date: 2010-06-16
forum: Multimedia Software
---

### Post by Rumpletumbler on 2010-06-16
My sound was working well on these sites and has suddenly started skipping. 

I've applied nothing other than system updates through update manager other than trying the ATI proprietary driver installed and then removed through Ubuntu Software Center. 

Worked great for 2 months and as I'm not on these sites daily I don't know what might have caused this.

Has anyone else experienced this?

---

### Post by Foxcow on 2010-07-13
I had a very similar problem in 9.10.  It turned out that pulse-audio was using 100% of one of my cores and caused the sound to skip.  I just killed the process in system monitor and restared any program(s) requiring sound.  It would happen every few hours sometimes.

No problems under 10.04 though.

---

### Post by Yellow Pasque on 2010-07-13
I'm not sure if Software Center removes Catalyst/fglrx properly, so:
```
sudo apt-get remove --purge fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
The first command may complain or not work, but it's okay. The second command is the important one.

---

