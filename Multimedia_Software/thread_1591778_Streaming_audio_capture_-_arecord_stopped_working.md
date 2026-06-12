---
title: "Streaming audio capture - arecord stopped working"
date: 2010-10-09
forum: Multimedia Software
---

### Post by akelsall on 2010-10-09
I had been using arecord from time to time to record a radio station, but now when I use it, it's not working. It is definitely capturing data, as I see the file size increment. However, when I try to play the file, I get nothing but silence.

My audio is definitely working, as I can play mp3s from my hard drive, and I can hear the streaming audio I'm trying to capture. Any thoughts? The syntax I'm using is:

arecord -f cd -d 3600 kshe &

3600 is the duration in seconds, kshe is the filename, and & just puts the process in the background.

Thanks,

Andy

---

