---
title: "Progam like camorama"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by lukasz21212121 on 2006-12-03
hi. i have got an aiptek web cam and i want to have a program which can capture and save movie/film from my camera. I'm looking for something like camorama, which works on my computer, but can only take photos. I want to record film, so i dont need any other functions. Camera works by USB.

---

### Post by javierfh on 2006-12-03
> **lukasz21212121 said:**
> hi. i have got an aiptek web cam and i want to have a program which can capture and save movie/film from my camera. I'm looking for something like camorama, which works on my computer, but can only take photos. I want to record film, so i dont need any other functions. Camera works by USB.

Hello,

what webcam do you have? i have aiptek too...and well i was wondering if it works fine for you with amsn?

I have used camorama and works fine and camstream as well.
But not sure if they can do what you want. I understood you want to record the video that you show with webcam, right?
One alternative i guess could be to use the camstream or camorama and capture the video with xvidcap for example.
xvidcap works perfectly, im amazed with it.

Hope that it helps, and would be nice to know what webcam you use and if it works fine for you with amsn(if you use it at all)

Javi

---

### Post by loell on 2006-12-03
xawtv :D

---

### Post by lukasz21212121 on 2006-12-03
xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
xinerama 0: 1280x1024+1280+0
xinerama 1: 1280x1024+0+0
WARNING: No DGA support available for this display.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct


i have installed camstream too, but it can take photos only.

I've installed STREAMER too, but i have got an error:
neither audio nor video format specified/found

:( what can i do?

---

### Post by loell on 2006-12-03
try this

```
xawtv -c /dev/video0 -remote

```

---

### Post by lukasz21212121 on 2006-12-03
i did.


now

 xawtv
This is xawtv-3.94, running on Linux/i686 (2.6.15-27-386)
xinerama 0: 1280x1024+1280+0
xinerama 1: 1280x1024+0+0
WARNING: No DGA support available for this display.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct


i see video after i resize window. now i try to record video.. i'm starting recording, and next i want to save.. and then next errors:


Oops: can't count up file names any more
Oops: can't count up file names any more
Oops: can't count up file names any more
rate: queueing frame twice (11)
Oops: can't count up file names any more
Oops: can't count up file names any more
rate: queueing frame twice (12)
Oops: can't count up file names any more
Oops: can't count up file names any more
rate: queueing frame twice (11)
Oops: can't count up file names any more
Oops: can't count up file names any more
rate: queueing frame twice (10)
rate: queueing frame twice (9)
Oops: can't count up file names any more
Oops: can't count up file names any more
Oops: can't count up file names any more
Oops: can't count up file names any more
etc....


instead of avi, it saves one image, and on image are many parts of one image in different places, or pixelized image... i vant an avi...

---

