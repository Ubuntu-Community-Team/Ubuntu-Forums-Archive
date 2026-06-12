---
title: "Recording Audio to Two Programs at Once"
date: 2011-09-06
forum: Multimedia Software
---

### Post by notkevin on 2011-09-06
I work at a university and I an scripting Ubuntu to automatically record lectures. We want to have both an audio-only (mp3) and an audio/video (mp4) version of each lecture. To keep things simple, I would like to record the mp3 using arecord and the mp4 using ffmpeg instead of trying to add the audio to the video after both have been recorded. When I try to record the audio with both programs I get the error "[alsa @ 0x96c41b0]cannot open audio device hw:0,0 (Device or resource busy)" on the program that starts second.  Is there any way to prevent arecord and/or ffmpeg from locking the device? Can the mic device be cloned so both programs can access the audio input using different alsa device ids? Any other suggestions? 

I am using Ubuntu 11.04. Thank you!

---

### Post by gordintoronto on 2011-09-06
Other suggestion: record the video, extract the audio from it.

---

### Post by notkevin on 2011-09-06
I was playing around with it some more, if I run ffmpeg first then run arecord it works but if I run arecord first then ffmpeg won't run.  I looked at the arecord man page and there is a --nonblock switch.  However even when I run:

/usr/bin/arecord -d 60 -f cd -t wav --nonblock /tmp/out.wav

I cannot run ffmpeg once arecord has started. Is the nonblock option broken, am I doing it wrong or does it not do what I think it does?

Thanks!

---

### Post by notkevin on 2011-09-06
> **gordintoronto said:**
> Other suggestion: record the video, extract the audio from it.

I have thought about that, but it going to be my last option.  The original scripts were written in AppleScript so I am trying duplicate their function exactly otherwise I need to rewrite a lot of code upstream. 

We are having cost cutting measures and I need to get the price of each computer under $300, which is not possible with Apple.

---

