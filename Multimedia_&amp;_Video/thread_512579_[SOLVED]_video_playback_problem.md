---
title: "[SOLVED] video playback problem"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by bskafh on 2007-07-29
Hello, i am a new ubuntu user and i am having a small problem playing my videos. I installed the codecs to play avi and other video files. When i play a video all i see is a black screen, i can hear everything though. I dont know if its a codec problem because the video worked fine for a few times, but it always went back to the black screen if i move the playback bar. i know its weird, but i really need help. thanks a lot in advance.

---

### Post by DC@DR on 2007-07-29
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626) -> Take a look at this intruction :-)

---

### Post by bskafh on 2007-07-29
hey, i did all the steps and i am still having the same problem. the video is playing but i cant see anything but a black screen.

---

### Post by bluecat9 on 2007-10-09
ALT+F2 > gstreamer-properties > Run > Video (tab)

Change "Plugin" to X Window System (No Xv) > Close

gl

---

### Post by kevinfitch83 on 2007-10-14
I was having the same problem and that fix worked for me. Thanks.

---

