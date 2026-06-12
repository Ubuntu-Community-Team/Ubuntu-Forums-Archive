---
title: "Recording specific window with ffmpeg?"
date: 2013-09-01
forum: Multimedia Software
---

### Post by josh17 on 2013-09-01
I was wondering if it was possible to record a specific window while record with ffmpeg via terminal? I'm trying to record minecraft gameplay but it does the whole screen, which I don't want because I play windowed mode.

I record using this command: ```
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /home/josh/videoTitle.mpg
```

Thanks to anyone who can help me out.

---

### Post by rai_shu2 on 2013-09-01
Someone [asked this]("http://askubuntu.com/questions/182944/how-can-i-record-an-opengl-game-in-ubuntu") almost exactly a year ago.

---

### Post by FakeOutdoorsman on 2013-09-03
See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719), specifically the section "Q: How do I get the exact size and coordinates of a specific window I want to capture?" (use xwininfo).

Do not use "-sameq": it [does not mean "same quality"](http://superuser.com/a/478550/110524).

---

