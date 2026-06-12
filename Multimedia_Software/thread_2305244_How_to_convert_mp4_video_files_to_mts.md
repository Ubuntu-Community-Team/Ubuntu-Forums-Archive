---
title: "How to convert mp4 video files to mts?"
date: 2015-12-04
forum: Multimedia Software
---

### Post by shamsat on 2015-12-04
How i can convert  mp4 or other video files to mts in ubuntu?

---

### Post by Bucky Ball on 2015-12-04
*Thread moved to **Multimedia Software**.*

You are wanting to convert files from a video camera? The first answer [here]("http://askubuntu.com/questions/73258/convert-mts-to-mpeg") might help. 

You might like to investigate Handbrake. I was under the impression it can deal with converting MP4. It's in Software Centre. From their site:

> Handbrake can process most common multimedia files and any DVD or BluRay sources that do not contain any kind of copy protection.

A search for 'convert mp4 mts ubuntu' might bring up some results also. Good luck.

---

### Post by andrew.46 on 2015-12-04
If you can get a decent copy of FFmpeg something like the following would be useful:

```

ffmpeg -i input.mp4 -c:v mpeg2video -qscale:v 2 -c:a mp2 -b:a 192k output.mts

```

This produced a decent output on my setup, thanks to Lou for [the syntax]("http://stackoverflow.com/questions/20078604/ffmpeg-conversion-to-mpeg2video")...

---

### Post by FakeOutdoorsman on 2015-12-04
Most consumer video cameras these days seem to use H.264 video and AC3 or some sort of PCM audio in MTS. Not sure why you want MTS, but from MP4 you could probably just remux:

```
ffmpeg -i input.mp4 -c copy -bsf:v h264_mp4toannexb output.mts
```

In this case note the use of the [h264_mp4toannexb bitstream filter](http://ffmpeg.org/ffmpeg-bitstream-filters.html#h264_005fmp4toannexb). Without it ffmpeg will provide an error telling you to use it.

---

