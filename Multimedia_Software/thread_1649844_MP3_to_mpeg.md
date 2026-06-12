---
title: "MP3 to mpeg"
date: 2010-12-20
forum: Multimedia Software
---

### Post by xXDestroyerGRXx on 2010-12-20
Hello,i want to convert a song and then upload to youtube

Is it possible?

---

### Post by ron999 on 2010-12-20
Hi
You can use a jpg picture with an mp3 song to make a video (a one-slide slideshow).

Use a command like this:-
```
ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy video.mp4
```

---

### Post by xXDestroyerGRXx on 2010-12-20
It worked !

---

### Post by xXDestroyerGRXx on 2010-12-20
No HD option. :(

---

### Post by ron999 on 2010-12-21
> **xXDestroyerGRXx said:**
> No HD option.:sad: 


.....;)

---

