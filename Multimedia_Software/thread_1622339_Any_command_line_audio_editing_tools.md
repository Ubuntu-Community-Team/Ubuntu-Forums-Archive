---
title: "Any command line audio editing tools?"
date: 2010-11-15
forum: Multimedia Software
---

### Post by jehiva on 2010-11-15
Hello all, 

Does anyone know of any good command line audio editing tools?  I would like one that can take an mp3 file and crop everything but the first 30 seconds or so (possibly decompressing those 30 seconds as well).

Thanks!

---

### Post by ron999 on 2010-11-15
Hi
ffmpeg will do the job.

Like this:-
```
ffmpeg -i filename.mp3 -t 30 -acodec copy output.mp3
```

If you want it 'decompressed' then use this command instead:-
```
ffmpeg -i filename.mp3 -t 30 output.wav
```

---

### Post by jehiva on 2010-11-15
Thanks ron999 you have solved my issue.

---

