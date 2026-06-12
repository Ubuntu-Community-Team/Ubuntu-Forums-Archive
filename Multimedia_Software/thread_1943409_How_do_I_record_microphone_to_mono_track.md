---
title: "How do I record microphone to mono track?"
date: 2012-03-19
forum: Multimedia Software
---

### Post by Splooshie123 on 2012-03-19
My microphone records to a stereo track and the sound ends up only coming out from the right channel. Any way to record to mono instead of stereo?

This screenshot shows the problem is with recording and not playback. Only the right channel is recording. The problem is that should be a mono recording and not stereo.
(No I do not live in Singapore. Yahoo's location tracking sucks.)

---

### Post by shantiq on 2012-03-20
hi splooshie     you can use sox   [in terminal]    > sudo apt-get install sox libsox-fmt-all



```
rec -c 1 -C 320  nameyouwant.mp3
```    for mp3  [-c 1 makes it mono]


```
rec -c 1   nameyouwant.flac
```   for flac  



Also  [**ogg **]("http://ubuntuforums.org/showpost.php?p=11056042&postcount=2")is good too

Then use ```
play nameyouwant.flac

```


to playback

---

### Post by Splooshie123 on 2012-03-21
Not exactly what I had in mind but thanks shantiq!

Following you suggestion, I discovered I can set Audacity to record to mono, too. Also, the recordings with sound only on the right channel can be split using Audacity into 2 mono tracks. I just delete the left channel and now I have 1 track that plays on both speakers.

Solved (sort of)

---

