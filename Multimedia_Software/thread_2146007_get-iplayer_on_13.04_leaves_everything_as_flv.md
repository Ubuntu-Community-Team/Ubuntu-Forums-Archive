---
title: "get-iplayer on 13.04 leaves everything as flv"
date: 2013-05-17
forum: Multimedia Software
---

### Post by shantiq on 2013-05-17
noticed that none of the conversions are being done on get-iplayer on 13.04


if i use tags like   --mkv   or say  ```
get-iplayer --mode=flashaacstd --aactomp3 --mp3vbr 0 --get 13322
```


i end up with an flv each time

not a huge problem but would be nice to fix

using    get_iplayer v2.82-25-g3547d05-ppa8

---

### Post by coldraven on 2013-05-17
Is get_iplayer looking for ffmpeg? I'm sure I read somewhere that 13.04 has replaced it with avconv or something.
Sorry, posting from 12.10 so I can't check. I keep meaning to upgrade but not getting around to it.

---

### Post by shantiq on 2013-05-17
haa   you have your thinking cap on Coldraven thank you


i installed ffmpeg with the guide [here]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")



and it requires linking


so


```
get-iplayer --mode=flashaacstd --aactomp3 --mp3vbr 0 --get 13322

```becomes


```
get-iplayer --mode=flashaacstd --aactomp3 --mp3vbr 0 --get 13322 **--ffmpeg "/usr/local/bin/ffmpeg"**

```



had never thought of it so grateful to you 
 prefer mkv and m4a/mp3 to flv  ::]]


shan

---

### Post by dinkypumpkin on 2013-05-22
FWIW, ffmpeg is in 13.04 package repo.  It's the libav version, so when you invoke it you get:

"*** THIS PROGRAM IS DEPRECATED *** This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

However, it still works with get_iplayer.  ffmpeg is in the "suggests" list for the get-iplayer package, so it's not automatically installed.

---

