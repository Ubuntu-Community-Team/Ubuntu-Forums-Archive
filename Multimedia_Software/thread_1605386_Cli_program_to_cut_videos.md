---
title: "Cli program to cut videos"
date: 2010-10-25
forum: Multimedia Software
---

### Post by rbutler on 2010-10-25
Hi there,

I have some 10hrs videos with around 6GB in size. Unfortunately avidemux2_cli runs into problems copying certain parts of it into an output file (frames get blur).

So I tried ffmpeg, but even if I use the sameq switch (same quality as source video),  the output video is not a 1:1 copy of the source video. In fact the output video is encoded again (and sound is not as in the source video) and that takes ages against a copy activity by avidemux.

Is there any other cli program for simply copying parts out of videos?

Thank you,
Ralf

---

### Post by FakeOutdoorsman on 2010-10-25
> **rbutler said:**
> So I tried ffmpeg, but even if I use the sameq switch (same quality as source video),  the output video is not a 1:1 copy of the source video. In fact the output video is encoded again (and sound is not as in the source video) and that takes ages against a copy activity by avidemux.

The FFmpeg *-sameq* option re-encodes your video.  You can use the *-vcodec copy* and *-acodec copy* options to simply copy the video and audio without re-encoding.  See this [example command](http://ubuntuforums.org/showpost.php?p=9395806&postcount=6).

In addition to the link, you may have to move the *-ss* option after the input for some sources.

---

### Post by rbutler on 2010-10-25
You're my hero ;)

---

