---
title: "Trying to hear two things at once."
date: 2008-05-06
forum: Multimedia Software
---

### Post by soundf on 2008-05-06
I tried to hear music from my music playlist(Totem Movie Player 2.22.1) and from a video at Youtube but i can't do both at the same time.

I saw the "Comprehensive Sound Problem Solutions Guide"
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449).
```

Getting more than one application to use the soundcard at the same time

    * You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available.

    *
      The setting is usually found under something like Tools >>> Configure >>> Player Engines.

    *
      For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver.

    *
      To do this you will need the alsa-oss package
      Code:

      sudo apt-get install alsa-oss

    *
      After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss.

```
I typed aoss firefox or aoss Totem Movie Player and i still couldn't make it work..

There's actually no way to hear two things at once unless i do some configuration with the softwares i want to hear from?

Thanks.

---

### Post by kpkeerthi on 2008-05-06
Try this.
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

