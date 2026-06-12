---
title: "Extracting Audio from Video (mp4)"
date: 2015-09-16
forum: Multimedia Software
---

### Post by james139 on 2015-09-16
I need to extract the mp3 files from a few speeches/talks recorded in mp4. I've tried [this method]("http://www.cyberciti.biz/faq/linux-unix-extract-audio-from-avi-video-file-online-stream/"), which initially seemed to work until I tried playing the files back and they wouldn't play. I have mp3 codecs etc but no luck. Has anyone got a different way of doing it?  Thanks.

---

### Post by howefield on 2015-09-16
I'm sure there are much better answers but for the few times I have had to do this, loading the file in Audacity then exporting to ogg/mp3 or whatever has worked fine.

---

### Post by james139 on 2015-09-16
Brilliant, thanks. Just what I was after.

---

### Post by howefield on 2015-09-16
Cool, glad it worked for you. :)

---

### Post by Yellow Pasque on 2015-09-16
Substitute 'avconv' for 'ffmpeg' if that's what your version of Ubuntu uses.
```
ffmpeg -i inputfile.mp4 -acodec copy outputfile.mp3
```

Please mark thread solved.

---

