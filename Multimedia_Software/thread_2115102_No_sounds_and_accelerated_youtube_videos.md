---
title: "No sounds and accelerated youtube videos"
date: 2013-02-11
forum: Multimedia Software
---

### Post by faustom on 2013-02-11
Hello,

since yesterday any sound has disappear and youtube videos are extremely accelerated (while videos with vlc have normal speed). I tried to remove and reinstall flash plugins but it didn't work.

This troubles started when I downloaded the "Aten project" program, but I don't know how to dis-install it..

Could anyone please help me...?

Thanks

---

### Post by Yellow Pasque on 2013-02-11
Try resetting pulseaudio config files with this command:
```
rm -r ~/.pulse*; pulseaudio -k
```

---

