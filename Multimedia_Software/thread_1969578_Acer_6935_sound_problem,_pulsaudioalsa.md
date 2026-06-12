---
title: "Acer 6935 sound problem, pulsaudio/alsa?"
date: 2012-04-30
forum: Multimedia Software
---

### Post by amiacamal on 2012-04-30
basically, plugging in headphones does not mute speakers. sound is duplicated, any ideas? 12.04, fully updated

---

### Post by amiacamal on 2012-05-02
24 hour bump, still no fix?

---

### Post by cortman on 2012-05-02
Would [this]("http://askubuntu.com/questions/128099/restore-speakers-headphones-option-in-ubuntu-12-04-solved") be of any help?

---

### Post by brainwash on 2012-05-02
Try to manually modify the sound module parameter like described in this post:

[http://ubuntuforums.org/showpost.php?p=10817185&postcount=14](http://ubuntuforums.org/showpost.php?p=10817185&postcount=14)

---

### Post by s.fox on 2012-05-02
Moved to [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334"), you might get more help in here :)

---

### Post by amiacamal on 2012-07-11
After giving up on the problem and coming back I rediscovered this thread, I have tried adding lines to the /etc/modprobe.d/alsa-base.conf  file so many times now that i dont know what the original was like anymore.

I also have no idea how to manually change that parameter...

---

