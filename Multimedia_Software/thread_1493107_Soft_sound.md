---
title: "Soft sound"
date: 2010-05-25
forum: Multimedia Software
---

### Post by 240r on 2010-05-25
I have an interesting issue. My belief is that my headphones are blown (slightly). Sound in Amarok, youtube, KMPlayer, etc are all very soft. However, it doesn't explain why the sound level is perfectly fine in Kaffeine.

I have master and front levels turned to max. I have HDA Nvidia. I only use headphones. It worked perfectly for years.

---

### Post by wieman01 on 2010-05-25
Is the sound level fine when you fire up Alsamixer via command line?

---

### Post by 240r on 2010-05-25
I am not sure what the levels in alsamixer should look like for it to be "fine". But I didn't touch alsamixer at all.

---

### Post by 240r on 2010-05-25
Just turned PCM all the way up in alsamixer. That seemed to fix it. Thanks!

Not sure how PCM got turned down. And why it affects everything but Kaffeine @_@

---

### Post by wieman01 on 2010-05-25
Don't ask me why, but it's a common problem. Glad you got it solved.

---

### Post by Mamarok on 2010-05-26
Well, unless you have the latest version of Kaffeine, it doesn't use Phonon yet, Amarok and Dragonplayer do.
Also, the sound level for the phonon-backend-xine is rather low, while the upcoming phonon-backend-vlc solves this issue. We plan a release of that new backend later this summer, so hopefully it will make its way into the Kubuntu backports PPA.

---

### Post by 240r on 2010-05-29
Mamarok, any clues for 
[http://ubuntuforums.org/showthread.php?t=1443260](http://ubuntuforums.org/showthread.php?t=1443260)
?

---

