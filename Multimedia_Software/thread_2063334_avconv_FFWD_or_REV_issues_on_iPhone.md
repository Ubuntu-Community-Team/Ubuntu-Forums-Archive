---
title: "avconv FFWD or REV issues on iPhone"
date: 2012-09-26
forum: Multimedia Software
---

### Post by razor7 on 2012-09-26
Hi, I'm using aconv to extract audio from some videos, but after some weeks ago, the MP3 seems to be ok, but when loaded into my iPhone 4, I can not fats forward or rewind the current track. It only happens eith recent aconv created MP3.

Any idea why?

avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1

Here is the command I use

avconv -i video.mp4 -ab 192k audio.mp3

Thanks a lot!

---

### Post by ron999 on 2012-09-26
> **razor7 said:**
> 
Here is the command I use
avconv -i video.mp4 -ab 192k audio.mp3

Hi
Maybe you need to do this...
Install the extra codecs:-
```
sudo apt-get install libavcodec-extra-53
```
Then:-
```
avconv -i video.mp4 -acodec libmp3lame -ab 192k -ar 44100 -ac 2 audio.mp3
```

---

### Post by razor7 on 2012-09-26
Well, tried with that command and the error persists, can't FFWD or REW on my MP3's.

Tested with Windows Pazera Free Audio Extractor 1.4 (with LAME 3.98.4) and the extracted MP3's works right.

I think is some kind of avconv issue

---

### Post by razor7 on 2012-09-27
Hi, using linux app "SoundConverter 1.5.4" the MP3 works completely right. Definitely is a avconv issue...

---

