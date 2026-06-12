---
title: "[SOLVED] script for audio ripping"
date: 2008-10-10
forum: Multimedia Software
---

### Post by SuperSonic4 on 2008-10-10
I'd like to rip the audio from flash files (flv) so that I can play them in amarok and sync them to iPod.

Currently I am running the following ```
ffmpeg -i input.flv -acodec copy output.mp3
```

but this only works for one at a time, ideally I'd like a batch whereby all videos are done and preferably given the same output title (ie file.flv to file.mp3). 

If it helps all videos downloaded go to ~/dwhelper

---

### Post by mc4man on 2008-10-10
While this was for something else 9batch convert mp3 to wma you could probably adapt to your use
[http://ubuntuforums.org/showthread.php?t=932627](http://ubuntuforums.org/showthread.php?t=932627)

---

### Post by sokopok on 2008-10-10
you could try:

cd ~/dwhelper
for i in *.flv; do ffmpeg -i "$i" -acodec copy "`echo "$i" | sed -r -e 's/(.*)\.flv$/\1.mp3/'`"; done

---

### Post by SuperSonic4 on 2008-10-11
Just what I was looking for, thanks muchly :D

---

