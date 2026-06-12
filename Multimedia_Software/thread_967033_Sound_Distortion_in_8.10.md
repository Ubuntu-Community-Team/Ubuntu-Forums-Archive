---
title: "Sound Distortion in 8.10"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Gipper P on 2008-11-01
Hi everyone,

I have recently upgraded from 8.04 to 8.10. Everything works fine, except my sound. Sounds do play, but they aren't right: it is distorted, especially at higher frequencies.
Never had this with Hardy, and I am at a loss as to where to start looking - have had a quick peek around here but it seems mostly like people who have problems with their sound have no sound at all...

Anyways, all ideas would be welcome!

James

---

### Post by Gipper P on 2008-11-02
Does anyone have any ideas?

---

### Post by d1rX on 2008-11-11
Also have this problem. Sound is over amped, can't find a solution. Using HDA Intel (alsa mixer) on IBM R61i

EIDT: Actually nevermind, turn down PCM a little (in alsa-mixer) and it all be good.

---

### Post by seanlano on 2008-11-19
Hi, thanks for that simple tip. I was having the same problem and it worked for me.

---

### Post by seanlano on 2008-11-19
Actually, should just mention, I ran ```
gnome-volume-control
``` and turned down PCM from there.

---

