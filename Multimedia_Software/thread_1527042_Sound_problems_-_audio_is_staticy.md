---
title: "Sound problems - audio is staticy"
date: 2010-07-08
forum: Multimedia Software
---

### Post by haran_hockey on 2010-07-08
Something is wrong with the audio on my laptop, when I used the live CD previously, nothing was wrong. It's all staticy when the base comes on or like a beat (I don't know how to explain it). Even youtube vids and such. My laptop audio is not usually like this, so any ideas?

---

### Post by lidex on 2010-07-08
Possibly overdrive distortion. Check your levels. I suggest gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by haran_hockey on 2010-07-08
Everything is enabled in sound card properties and I dunno what to do with the main controls. I guess a screenshot may help.

[http://i251.photobucket.com/albums/gg288/haran_hockey/alsamixer.png]("http://i251.photobucket.com/albums/gg288/haran_hockey/alsamixer.png")

---

### Post by lidex on 2010-07-08
Try turning master and pcm down to about 3/4

---

### Post by haran_hockey on 2010-07-08
WOW, that's crazy. What exactly is PCM, turning it down to around 75 % worked, didn't even need to bring down the master

---

### Post by lidex on 2010-07-10
Great - easy fix! Would you please mark the thread as solved using 'Thread Tools' up top? Thanks. :grin:

---

