---
title: "skype webcam upside down"
date: 2014-07-08
forum: Multimedia Software
---

### Post by sn0m on 2014-07-08
Hi
Just installed 14.04 64 bit.
Skype webcam is upside down.
When i used locate libv4l, this is what i get:
/usr/lib/x86_64-linux-gnu/libv4l
Does anyone know how to sort this annoying thing?
Many thanks for your help
sn0m

---

### Post by patsev-anton on 2014-07-12
try 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

