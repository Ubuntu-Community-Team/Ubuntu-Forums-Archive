---
title: "Cannot play 5:1 audio on Blu-ray or HD-DVDs"
date: 2010-03-17
forum: Multimedia Software
---

### Post by timmy_c on 2010-03-17
I've been trying to play the Transformers 2 Blu-ray DVD on Ubuntu Karmic Koala 64-bit. I followed the steps on [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD) but when I play the movie using mplayer I can only get the 2:1 audio tracks to play e.g. directors commentary, non-english languages. I cannot get mplayer to detect the 5:1 English track. I tried VLC, which can detect the English audio track, but when I select it I just get silence.

I have also tried to play the Serenity HD-DVD but have a similar problem.

This is the command I am using to play the movie in mplayer...
```
mplayer -vc ffvc1 -vo x11 BDMV/STREAM/00010.m2ts
```...then I switch between audio tracks by right-clicking the mplayer window.

Please can you suggest any reasons why I am unable to play the English audio track.
Thanks

---

