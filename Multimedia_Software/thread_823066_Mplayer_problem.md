---
title: "Mplayer problem"
date: 2008-06-08
forum: Multimedia Software
---

### Post by nasosnik on 2008-06-08
I am using Mplayer for playback of .avi files and i have installed w32codecs and the codecs that are provided from Mplayer official site.At some .avi files i get the error message "frame sync error" and at some others the movie picture is corrupted with a green line.I am attaching a screenshot of the problem.

---

### Post by zain3000 on 2008-12-11
I was having the same problem with some .avi files when it came to the "frame sync error".

I fixed it by changing the audio codec family from FFmpeg/libavcodec audio decoders to AAC (MPEG2/4 Advanced Audio Coding).

Try that and see how it works (Preferences -> Audio codec family)

---

### Post by moonese on 2009-03-15
This works for me, Thanks!

---

