---
title: "No sound when playing Youtube and Vlc player"
date: 2008-10-20
forum: Multimedia Software
---

### Post by brhs on 2008-10-20
I am new to Linux system and using Ubuntu now. I have a problem that when I play a video on Youtube, there is a sound .
But at the same time, when I play music on either Mplayer or VLC
or any other media player, it would not works.
So, What should I change or what should i do to make it perfect.

Sound : Youtube --> works
        MPlayer or and other players --- > not works


Thanks

---

### Post by Afkpuz on 2008-10-20
Might be something else, but the normal ubuntu sound driver (ALSA) does not allow 2 audio streams to be played at once.  try closing your browser and everything that can make noise and then try rhythmbox.  Still no sound?

---

### Post by wolfen69 on 2008-10-20
```
sudo apt-get install libflashsupport
```
should fix it.

---

