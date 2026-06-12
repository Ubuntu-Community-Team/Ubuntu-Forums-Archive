---
title: "Some sounds work, others don't."
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by Sukarn on 2006-12-19
I have an ASUS A8V-VM board with an onboard sound card, that made high pitched noise whenever I played any sound file. Well, that was fixed with the instructions in the thread [http://ubuntuforums.org/archive/index.php/t-260352.html](http://ubuntuforums.org/archive/index.php/t-260352.html).

But, unlike my friend's PC, I am unable to get mp3 preview by mouse over on mp3 files (haven't tried other file types). I have the codecs installed as well as the mpg321 and vorbis-tools packages. I have also tried replacing mpg321 with mpg123, mpg123-esd, mpg123-alsa. None worked. Neither do I get the login and logout sounds.

Also, I am unable to play more than one sound file at the same time.

If I play a high bitrate sound file ***in RealPlayer***, I get quite a messed up sound from the system (It sounds as if I am playing a high pitch sound with a lot of base instead of the pitch. The sound shifts too much toward the base.). **EDIT:** This one seems true only for RealPlayer.

It all works fine in windows xp, so I know that the hardware is not faulty.

Any help is appreciated.

---

### Post by Sukarn on 2006-12-21
*bump*
Doesn't anyone know of a way to fix this?

---

### Post by 3rdalbum on 2006-12-21
The audio Preview function is driven by Sox:

```
sudo apt-get install sox
```

I don't know about your other sound problems, but usually if you can't hear Login and Logout sounds, it means that ESD is turned off. Try checking the Sound preferences panel.

---

### Post by Sukarn on 2006-12-27
I just re-installed Ubuntu after a quick format, but the problem still remains. ESD is also turned on, but I still have all of the problems I mentioned above (including being unable to play the sound files with mouse over - I have also tried installing sox).

---

