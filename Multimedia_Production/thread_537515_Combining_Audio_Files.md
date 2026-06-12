---
title: "Combining Audio Files"
date: 2007-08-29
forum: Multimedia Production
---

### Post by rharriso on 2007-08-29
I have MP3 files of a book on tape. I'd like to make few files just for ease of use. How would I combine the files? Is there a program? Would the cat command work just fine?

---

### Post by variona on 2007-08-29
[http://www.mpex.net/software/details/mp3directcut.html](http://www.mpex.net/software/details/mp3directcut.html) is a windows application that is free and works fine under wine.
variona

---

### Post by rsambuca on 2007-08-29
Yes, the cat command works perfectly for mp3s.

```
cat file1.mp3 file2.mp3 file3.mp3 > outputname.mp3
```

---

### Post by rharriso on 2007-08-30
Thanks a lot, I think I'll go with the cat method. It makes me feel like a big kid.

---

### Post by vanadium on 2007-08-30
The cat command might seem to work, but you end up with files with wrong mp3 headers and headers in between the audio data. mp3 playback software will either play a small pop or skip over it. The utility mp3wrap will "wrap" several mp3s in one playable file. If you change your mind later, you can restore the original mp3s using mp3splt.

---

### Post by rharriso on 2007-08-31
Thanks for the save buddy.

---

