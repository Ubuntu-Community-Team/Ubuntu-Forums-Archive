---
title: "mplayer how to move to a time point"
date: 2010-10-06
forum: Multimedia Software
---

### Post by bill-lancaster on 2010-10-06
Is it possible (by command line) to move forward to a time point in an audio file?

---

### Post by ron999 on 2010-10-06
Hello again.

mplayer has the **-ss** option like ffmpeg.
It's used either with seconds or hh:mm:ss.

Examples.

Like this:-
```
mplayer -ss 180 filename.mp3
```

Or like this:-

```
mplayer -ss 00:03:00 filename.mp3
```

---

### Post by genjuroSE on 2011-07-24
Thanks Ron!
Was looking for this too :)

---

### Post by SeijiSensei on 2011-07-24
SMPlayer supports a Ctrl+J command that immediately moves to a particular timestamp.  I tried using that with mplayer itself running from the command prompt, but it doesn't work.  I did a quick scan of the mplayer man page and didn't see any jump option in the list of keyboard control options either.

---

