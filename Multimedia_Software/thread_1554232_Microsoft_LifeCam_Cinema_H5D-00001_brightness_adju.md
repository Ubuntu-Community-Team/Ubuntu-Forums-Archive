---
title: "Microsoft LifeCam Cinema H5D-00001 brightness adjustment"
date: 2010-08-16
forum: Multimedia Software
---

### Post by as400 on 2010-08-16
Folks,

I've seen several posts about adjusting the brightness on webcams within Ubuntu going through /sys/module/... /parameters/ however, I need directions for the Microsoft LifeCam Cinema specifically.

It runs well with Skype but during the day the image is way too bright so I look like a ghost on cam.

I'm running with UBUNTU 10.04 LTS *Lucid Lynx* on a DELL D620 laptop.

Any help pointing me to the right direction is appreciated.

ED

---

### Post by AKADAP on 2010-08-16
> **as400 said:**
> Folks,

I've seen several posts about adjusting the brightness on webcams within Ubuntu going through /sys/module/... /parameters/ however, I need directions for the Microsoft LifeCam Cinema specifically.

It runs well with Skype but during the day the image is way too bright so I look like a ghost on cam.

I'm running with UBUNTU 10.04 LTS *Lucid Lynx* on a DELL D620 laptop.

Any help pointing me to the right direction is appreciated.

ED

Get the Video4Linux Control Panel installed, and mess with the "Exposure, Auto" setting.
I found that one of the video capture tools (forgot which one) changes this setting to a fixed exposure. It left me with a white screen and thinking that the camera was not working. Took me a while to find the setting and get it set back to "Aperture Priority Mode".

---

### Post by as400 on 2010-08-16
tyvm AKADAP
I will work on the settings and let you know. I've set it to Aperture Priority Mode right now.

---

### Post by as400 on 2010-08-17
In Video4Linux where EXPOSURE,Auto -  I can only set to either Manual or Aperture Priority Mode but never to AUTO. It gives me the following error message:

Unable to Set Control:
Unable to set Exporure, Auto Input/output error

I can however tweak the brightness but as the day goes by I have to change it so at night my video is not dark.

Any ideas on how to get the AUTO setting to work so exposure is automatic?

---

### Post by no2498 on 2010-08-17
cheese is to have all the setting's for webcams
you can change settings in cheese

hope this helps

---

### Post by AKADAP on 2010-08-17
> **as400 said:**
> In Video4Linux where EXPOSURE,Auto -  I can only set to either Manual or Aperture Priority Mode but never to AUTO. It gives me the following error message:

Unable to Set Control:
Unable to set Exporure, Auto Input/output error

I can however tweak the brightness but as the day goes by I have to change it so at night my video is not dark.

Any ideas on how to get the AUTO setting to work so exposure is automatic?

"Aperture Priority" IS an auto mode.

---

### Post by AKADAP on 2010-08-17
> **no2498 said:**
> cheese is to have all the setting's for webcams
you can change settings in cheese

hope this helps

except for me, cheese is broken. Won't record video with sound, hangs instead. Will record video without sound if I misconfigure the audio input.

---

### Post by no2498 on 2010-08-17
ok try the settings in ekiga softphone

or this program may help you wxcam
read and install the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope that helps

---

### Post by as400 on 2010-08-18
> **AKADAP said:**
> "Aperture Priority" IS an auto mode.

AKADAP thanks for the clarification. I dont see an automatic change in this mode occur with hight or low light however.

---

