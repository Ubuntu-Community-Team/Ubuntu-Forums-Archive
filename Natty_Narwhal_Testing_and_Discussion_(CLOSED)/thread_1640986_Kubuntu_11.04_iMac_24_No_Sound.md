---
title: "Kubuntu 11.04 iMac 24 No Sound"
date: 2010-12-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-12-08
Hi All

I'm using an iMac 24" dual core 2008 model, 4GB RAM 2.4GHZ. I'm using kubuntu 11.04 Alpha1. I can not for the life of me get the sound working. I've appended /etc/modprobe.d alsa-base.conf with 
snd-hda-intel model=imac24"
and still no sound. 

output of lspci
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

---

### Post by lidex on 2010-12-08
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by cariboo on 2010-12-09
Have you started alsa-mixer in a terminal, just to make sure all the volume controls are turned up?

---

