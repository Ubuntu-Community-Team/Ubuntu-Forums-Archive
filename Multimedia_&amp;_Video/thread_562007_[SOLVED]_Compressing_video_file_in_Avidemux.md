---
title: "[SOLVED] Compressing video file in Avidemux"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by miguelan on 2007-09-28
Recently, I made a video with a digital camera and its size is about 25 Mb. I want to send it by email and therefore I want to reduce it. Using Avidemux, I suceed in making it smaller and applying some filters to make it nicer, cropping, etc. However, when I try to open it in Windows Media Player, it only displays the sound and not any image. I've read some other posts related to this subject, but my problem is not solved yet. 
Regarding Avidemux, I have a couple of questions:
1. Which filter or codec should I use? I see a long list, and I do not know which one is the appropriate one.
2. Avidemux is not recongnizing .srt files for subtitles. Could anyone describe step by step how to create subtitles for videos? By an unkwon reason, I'm not succesful installing jubler on my Ubuntu.

Thanks in advance,


Miguel

---

### Post by pay on 2007-09-28
You need the codecs installed in windows for the file to play the video. ffdshow can decode most formats in media player, or use vlc.

Choosing the right codec can be more difficult. The best quality would be (imo) h.264 (x264) + Vorbis with  matroska container, but would mean that it would be harder to play on a windows box. xvid + mp3 (lame) would have decent quality and decent playability. You could also go the patentless route with theora.. (should play with ffdshow or vlc)

The only formats that will play without ffdshow (or other codecs) on a clean windows installation are wmv and mpg, wma and mp3.

---

### Post by miguelan on 2007-10-13
Thanks a lot for the useful info. I managed to do it, although the "Vorbis" Audio Filter gave me errors when trying to save the video. However, the "Lame" Filter worked fine.


Miguel

---

