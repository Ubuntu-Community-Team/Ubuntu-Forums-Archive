---
title: "decompressing an mp4?"
date: 2009-09-27
forum: Multimedia Software
---

### Post by LowFidelity on 2009-09-27
I was wondering if there is any way to convert an mp4 into a dv or an avi file without any quality loss. I know kino has the capacity to convert as such, but I lose some quality in the process.

---

### Post by squaregoldfish on 2009-09-27
Try mplayer - I use this to convert compressed audio to wav:

```
mplayer -ao pcm:fast:file=out.wav in.mp4
```

Steve


Ignore this - it's for audio only. D'oh.

---

### Post by mcduck on 2009-09-27
> **LowFidelity said:**
> I was wondering if there is any way to convert an mp4 into a dv or an avi file without any quality loss. I know kino has the capacity to convert as such, but I lose some quality in the process.

Sorry, but no. Converting a compressed file from one compression to other will always reduce the quality.

However .avi is just a container file, not a compression, so it is possible to repackage your MP4-encoded video into .avi container without re-encoding the video. Not that doing so would gain you much, unless you have some media player that supports MP4 encoding but not MP4 container.

---

### Post by LowFidelity on 2009-09-27
well, the reason why I wanted to do something like this is because I have a camcorder that records in .mp4, but I believe I need an uncompressed video format if I want to edit anything. 

is there an "uncompressed" video format that I could convert to?

---

### Post by squaregoldfish on 2009-09-27
OK, my second try!

mplayer again:

```
mencoder -oac pcm -ovc raw -ofps 25 -noskip -o /Media/$1.dv $1
```

Alter the frame rate as required.

Steve.

---

### Post by LowFidelity on 2009-09-28
thanks! all I had to change was the -ovc to libdv!

---

