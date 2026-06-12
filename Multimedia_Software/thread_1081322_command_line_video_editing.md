---
title: "command line video editing"
date: 2009-02-26
forum: Multimedia Software
---

### Post by meg23 on 2009-02-26
I have a bunch of flash videos that I want to batch edit. I want to delete the first 3 seconds off of every flash file. Is it possible to do this with an ffmpeg or a mplayer script? It would save me a lot of time.

---

### Post by eldragon on 2009-02-26
transcode or mencoder?

---

### Post by meg23 on 2009-02-26
I looked for the man pages for both mencoder and transcode and I couldn't really find what I was looking for. Both of those man pages are enormous. Anyone who can parse me a script?

---

### Post by FakeOutdoorsman on 2009-02-26
You can do this with FFmpeg:
```
ffmpeg -ss 00:00:03:00 -i input.flv -acodec copy -vcodec copy output.flv
```
[list][*] **ss**: the time offset from beginning.
[*] **acodec copy**: copy the audio stream instead of re-encoding
[*] **vcodec copy**: copy the video stream[/list]
Copying the streams will preserve the quality and save time since there will be no re-encoding.

---

