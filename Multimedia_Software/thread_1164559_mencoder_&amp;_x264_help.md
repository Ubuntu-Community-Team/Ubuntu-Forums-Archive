---
title: "mencoder &amp; x264 help"
date: 2009-05-19
forum: Multimedia Software
---

### Post by steve51184 on 2009-05-19
hi all i'm trying to get mencoder working to convert a video along with an intro video (so essentially joining two videos but this will be for many files all with the same intro file) but i can't seem to find any good guides out there

here's what i want:

video: x264 @ 200kbs
audio: lame mp3 22050 Hz stereo @ 64kbs cbr
resolution: 512:384
framerate: 23.976
container: avi

and i want to mp3 converting and video converting to be as fast as possible (i know there are options to speed it up) and also to have multi-core support if available

please help

---

### Post by shirilover on 2009-05-20
H.264 video, which is what x264 creates, is not compatible with avi as a container without hacks.

If you must use avi, then I suggest xvid4 as the video codec. Or, you could use a matroska container (mkv) instead.

---

### Post by steve51184 on 2009-05-20
well i use mediacoder and that has avi as a container for x264 video

anyway can i get some help on this please?

---

### Post by xzero1 on 2009-05-20
You could probably convert with ffmpeg but to join the files and convert I would try something like avidemux. See [http://avidemux.sourceforge.net/](http://avidemux.sourceforge.net/) for more information.

---

### Post by steve51184 on 2009-05-20
why not just do something like this not not use multiple programs?

```
mencoder -o output.avi -oac mp3lame -lameopts cbr:br=64 -srate 22050 -ovc x264 -x264encopts bitrate=200 threads=auto -ofps 23.976 input1.avi input2.avi
```

---

