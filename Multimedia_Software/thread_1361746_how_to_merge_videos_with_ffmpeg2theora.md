---
title: "how to merge videos with ffmpeg2theora?"
date: 2009-12-22
forum: Multimedia Software
---

### Post by Lucas Malor on 2009-12-22
Hello. Is there a way to merge more video files in one streaming and convert it with [ffmpeg2theora]("http://v2v.cc/%7Ej/ffmpeg2theora/")?

---

### Post by Jose Catre-Vandis on 2009-12-22
This sounds like a two stage process. First convert all your video files to ogg/theora
```
ffmpeg2theora videofile.ext
```

Then I would use mencoder (part of mplayer) to concatenate them:
```
mencoder -o output.ogg -oac copy -ovc copy file1.ogg file2.ogg
```

---

### Post by Lucas Malor on 2009-12-30
Thank you. I have another question, I posted it [here]("http://ubuntuforums.org/showthread.php?t=1368243")

---

