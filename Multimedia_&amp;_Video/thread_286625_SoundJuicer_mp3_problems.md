---
title: "SoundJuicer mp3 problems"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by rkakkar on 2006-10-28
Sound Juicer is not extract the cd into mp3 format. please see the screenshot attached for the error message.

my mp3 profile is as follows:

Gstreamer: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux

extension: mp3

---

### Post by aysiu on 2006-10-28
I know this isn't the answer you're looking for, but after using Sound Juicer and Goobox, I've been pretty happy with Grip.

---

### Post by La muerte del DIos on 2006-11-05
I know your string is useful because I just test it. Just change the **196 **to **192**. Works perfectly for me. And also thanks, i recently upgrade to edgy and was searching for the string. :D Hope it works also for you.

---

