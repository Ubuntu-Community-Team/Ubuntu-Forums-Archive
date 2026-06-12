---
title: "Flac -&gt; Aac / Mp4 / M4a"
date: 2007-11-02
forum: Multimedia Production
---

### Post by Tlon on 2007-11-02
Hopefully this question has a fairly simple answer.

I backup all of my CD's in FLAC format.  I need a program that will convert from FLAC to AAC, preferably without losing ID3 tags in the process (these ones are for play on my iPod).  That's all.

---

### Post by MrFSL on 2007-11-02
the tags will be the problem but ffmpeg and mencoder can do the conversions.

---

### Post by daengbo on 2007-11-02
ffmpeg -i test.flac test.aac
You'll have to edit the tags, I guess.

---

### Post by Creative2 on 2007-11-02
mmm i don t know if id3 are saved but i have made a gui for ffmpeg and mencoder so if they  do it ok if don t =) i am sorry here the link [http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by cozmic charlie on 2007-11-05
Try PACPL ([http://viiron.googlepages.com/](http://viiron.googlepages.com/)) - it handles a wide range of both audio and video files and allows you to tag and convert at the same time.

---

