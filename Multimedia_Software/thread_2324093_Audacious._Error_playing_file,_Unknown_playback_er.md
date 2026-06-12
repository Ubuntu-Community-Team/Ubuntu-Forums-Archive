---
title: "Audacious. Error playing file, Unknown playback error"
date: 2016-05-10
forum: Multimedia Software
---

### Post by tuese on 2016-05-10
Xubuntu 16.04.
```
ERROR mpg123.cc:285 [print_mpg123_error]: mpg123 error in file:///media/main/Music/Diane%20%26%20David%20Arkenstone/Enaid%20-%20Guinevere%27s%20Tears.mp3: Failed to find valid MPEG data within limit on resync. (code 28)
ERROR util.cc:160 [audgui_simple_message]: Error playing file:///media/main/Music/Diane%20%26%20David%20Arkenstone/Enaid%20-%20Guinevere%27s%20Tears.mp3:
Unknown playback error
```
I get an error, but song is played. The issue only with Audacious, the other players play fine. Error occurs even with a new files. What is the problem and how to fix it?

---

### Post by andrew.46 on 2016-05-11
There is a work around rather than a fix: disable the mpg123 plugin in the preferences and enable the FFmpeg plugin....

---

### Post by tuese on 2016-05-11
Thank you. I already did it. Then it is a bug?

---

### Post by asatbluesboy on 2016-12-06
Thank you! Disabled MPG213, reset Audacious and problem solved on 16.04

---

### Post by Yellow Pasque on 2016-12-06
[http://redmine.audacious-media-player.org/issues/628](http://redmine.audacious-media-player.org/issues/628)

---

