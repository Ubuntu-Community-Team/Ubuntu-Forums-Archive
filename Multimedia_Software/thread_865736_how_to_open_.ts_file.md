---
title: "how to open .ts file"
date: 2008-07-20
forum: Multimedia Software
---

### Post by afeasfaerw23231233 on 2008-07-20
i opened it with vlc and there was only sound but no image. how can i open .ts file? what are those " .ts "? thanks!

---

### Post by mcduck on 2008-07-21
.ts is MPEG Transport Stream.

You'll probably have to convert it into normal MPEG file with some program. I donät know what tool would do the trick in Linux..

edit: It seems that mencoder should be able to do this:
```
mencoder -of mpeg -ovc copy -oac copy -o test.mpg test.ts
```

---

### Post by afeasfaerw23231233 on 2008-07-21
thanks

---

### Post by xc3RnbFO8P on 2008-07-21
In Synaptic Package Manager search **TS streamer**,
good, bad and the ugly.

EDIT:
If still dosnt play, rename the video *.m2t

---

