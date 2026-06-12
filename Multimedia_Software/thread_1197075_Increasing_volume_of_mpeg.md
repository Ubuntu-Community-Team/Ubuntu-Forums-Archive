---
title: "Increasing volume of mpeg"
date: 2009-06-25
forum: Multimedia Software
---

### Post by Dark Aspect on 2009-06-25
Hello,

How do I increase the volume of an mpeg without loss in quality? Meaning I copy the format over from its source, but have the software volume higher. Should I use Avidemux or mencoder? I am playing the mpeg through mplayer but I have to turn the volume to a ridiculous level to hear anything.

---

### Post by andrew.46 on 2009-06-27
Hi Dark Aspect,

> **Dark Aspect said:**
> How do I increase the volume of an mpeg without loss in quality? Meaning I copy the format over from its source, but have the software volume higher. Should I use Avidemux or mencoder? I am playing the mpeg through mplayer but I have to turn the volume to a ridiculous level to hear anything.

There is another choice which is to use FFmpeg's *-vol* option:

```
-vol volume         change audio volume (256=normal)
```

so you could try something like:
```

ffmpeg -i *infile.mpg* -vcodec copy -acodec copy -vol 384 *outfile.mpg*
```

but be prepared to experiment a little with this exact '-vol' value as too little is a waste of time and too much will probably introduce distortion.

**Edit:** Oops!! As mc4man has discreetly pointed out to me '-vol' does not work with '-acodec copy'. My apologies for talking rubbish :-). 

All the best,

Andrew

---

### Post by bobince on 2009-06-27
> How do I increase the volume of an mpeg without loss in quality?

I've done this before by demuxing MP3 audio from the MPEG, running it through a non-recoding MP3 volume altering tool, then remuxing the audio back into the file.

(I used AVIdemux for the muxing, and MP3DirectCut on Windows to change the volume, but I'm guessing mp3gain on Linux would work just as well.)

---

