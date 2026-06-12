---
title: "RadeonHD OSS Driver problems"
date: 2009-07-26
forum: Multimedia Software
---

### Post by nSTER on 2009-07-26
After following the guide at [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) I managed to successfully get the RadeonHD driver working but I am having problems with the opengl rendering. 

```
glxinfo | grep "renderer string"
returns
My OpenGL renderer string: Software Rasterizer
```

I have a Radeon HD 3870 which has the RS670 GPU according to the article it should return "Mesa DRI". I have attached my xorg.0.log file for reference.

---

### Post by igorzwx on 2009-07-26
There migh be a conflict between OSS driver
and ALSA drivers.
Usually, they do not like each other

---

### Post by nSTER on 2009-07-26
Sorry for asking but how is there be a relation to sound drivers to the video card? If there is actually a problem with the sound drivers how might I tackle it? 

EDIT: I added one to many "S" in the title sorry for the confusion

---

### Post by igorzwx on 2009-07-26
no problem.

many people arrive now without sound

---

### Post by igorzwx on 2009-07-26
type on terminal:

top

---

### Post by Yellow Pasque on 2009-07-26
Your card is based on an R**V**670. The section of the article you're referring to only applies to Radeon X1k and the 690G onboard/IGP (and its variants). There is no open-source 3D hardware acceleration for RV6x0/RV7x0 cards yet, so it should say "Software Rasterizer".

---

### Post by nSTER on 2009-07-26
Darn, thanks for clearing that up.

---

