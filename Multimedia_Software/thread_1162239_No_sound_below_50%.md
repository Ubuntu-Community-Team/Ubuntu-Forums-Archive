---
title: "No sound below 50%"
date: 2009-05-17
forum: Multimedia Software
---

### Post by dapaintballer331 on 2009-05-17
I have a fresh insstall of Jaunty, on a Gateway Laptop (1 year old), but I didn't have this problem on my last install of Juanty or Gutsy.

When I set my system sound below maybe 50 or 60%, no sound comes out of the speakers.

Is there some way to adjust the scale? Max volume is true max volume, but its very difficult for me to currently pick a reasonable volume, since increments in volume are huge.

---

### Post by VastOne on 2009-05-18
> **dapaintballer331 said:**
> I have a fresh insstall of Jaunty, on a Gateway Laptop (1 year old), but I didn't have this problem on my last install of Juanty or Gutsy.

When I set my system sound below maybe 50 or 60%, no sound comes out of the speakers.

Is there some way to adjust the scale? Max volume is true max volume, but its very difficult for me to currently pick a reasonable volume, since increments in volume are huge.

In terminal run

alsamixer

check that your Front setting is at 100%

---

### Post by xyepblra on 2009-06-06
> **VastOne said:**
> In terminal run
```
alsamixer
```
check that your Front setting is at 100%
Thank you for your advise, but does that really help adjusting the increment of the volume scale?
It is the problem I tried to describe [here]("http://ubuntuforums.org/showthread.php?t=1131958"), but no result so far...

---

### Post by tolotos on 2009-06-08
I am certain that I have read about a solution to this somewhere before, but unfortunatly I can`t find the site any more :-(. But haeds up, at least there is a solution ;-). Until you find it or someone posts it here, i would suggest adding volume-control to your gnome or kde panel. Therby you can adjust audio levels, just a bit slower than by your audio-buttons. 

Another option would be to make your applications use pulsaudio, while you addust the levels of the alsamixer with the sliding scale. Thereby you could adjust the maximal volume to your liking.

---

### Post by treesurf on 2009-06-08
I have the same problem with my Gateway laptop. :(

---

