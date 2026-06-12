---
title: "how to play mkv files by Movie Player?"
date: 2009-01-01
forum: Multimedia Software
---

### Post by lidengdeng on 2009-01-01
My ubuntu version is 8.04. 

But the Movie Player could not play .mkv medie. 

Any help? thanks.

---

### Post by mikull on 2009-01-01
did u try it out on vlc?
i am able to play mine on vlc in hardy

---

### Post by steeleyuk on 2009-01-01
MKV is a container format for other formats. So, in effect you'll need to install the related codecs which are stored in the MKV. This could be Xvid, DivX, MPEG, H.264, etc for video. It also can handle many different audio formats, MP3, AAC, etc.

So, you'll want to install the Gstreamer bad and ugly codecs to make sure you cover all the above.

*sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly*

Hopefully, that will be enough to get the MKV playing in Totem.

---

### Post by lidengdeng on 2009-01-01
Thanks for suggestions.

After I installed vlc, but there is no screen. I could only hear the voice, no picture right now.

What should I do next?? thx.

---

### Post by CompactDestruction on 2009-01-01
Find out what codec the video is in.

---

