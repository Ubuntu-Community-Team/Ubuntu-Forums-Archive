---
title: "[SOLVED] change bit-rate in ffmpeg"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by adityakavoor on 2008-02-26
How do I change the bitrate of media files that I convert to mp3 using ffmpeg ??

By default it gives 64 kbps that reduces the quality very much.

I want it to be atleast 128 kbps , If possible by default .

Any Idea ?? :confused:

---

### Post by ron999 on 2008-02-26
Hi
Your command should be something like this:-

[B]ffmpeg -i <filename> -acodec mp3 -ab 128k -ac 2 -ar 44100 <outputname.mp3>
[/B]
<filename> is the input file
-acodec is the codec used
-ab is the bitrate
-ac is 2 channels (stereo)
-ar is samplerate
<outputname.mp3> is the output file
:guitar::guitar:

---

### Post by adityakavoor on 2008-02-26
Superb ron999 

Thank you :popcorn:

---

