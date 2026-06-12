---
title: "Converting Video to Audio  (How?)"
date: 2011-11-17
forum: Multimedia Software
---

### Post by glennbates on 2011-11-17
I have some videos that I would like to record the audio from to make a ring tone and other things.  What software can do this?

---

### Post by MoreOrLess on 2011-11-17
ffmpeg. For example, to demux to an mp3 (make sure you have lame installed first)```
ffmpeg -i *infile* <OPTIONS> *outfile.mp3*
```

---

### Post by dniMretsaM on 2011-11-17
Most graphical converters (such a SoundConverter and soundKonverter) are smart enough to do this if you specify the output as OGG Vorbis or other audio format. A few obscure converters will through an error. If you prefer command line tools, use FFmpeg as mentioned above.

---

