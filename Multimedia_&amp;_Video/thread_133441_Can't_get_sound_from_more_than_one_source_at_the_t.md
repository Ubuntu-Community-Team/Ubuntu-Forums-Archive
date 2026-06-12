---
title: "Can't get sound from more than one source at the time"
date: 2006-02-20
forum: Multimedia &amp; Video
---

### Post by tafsen on 2006-02-20
When I play music from amaroK, I can't get sound from VLC.  How can I fix this?

---

### Post by jack frost on 2006-02-20
I am having that same problem.  I have my music playing, then when I go to another workspace and play a video, I see the video but no sound.  I am new to linux so any help is appreciated.
:D

---

### Post by Crayoneater on 2006-02-20
assuming you are using the alsa driver, you need to edit the .asoundrc file i think....you need to set it up to use dmix...go to [http://alsa-project.org](http://alsa-project.org) for more information....check out the soundcard list and see if it has anything about your soundcard...i think that is the problem....

---

