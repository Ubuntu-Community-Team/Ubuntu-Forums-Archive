---
title: "webm to mp3 Conversion?"
date: 2012-03-04
forum: Multimedia Software
---

### Post by Arthdoeth on 2012-03-04
Any ideas how I can convert .webm format to .mp3. ffmpeg is only an encoder for the format not a decoder.

Many Thanks

Will

---

### Post by papibe on 2012-03-04
Latests version of VLC can decode and encode webm. Depending on what Ubuntu version are you using, you may already have a version that can do it.

There is also an app called Arista Transcoder, that I know can code webm. It could be interesting to check if it can decode too.

Just some thoughts,
Regards.

---

### Post by FakeOutdoorsman on 2012-03-06
ffmpeg should be able to decode it and create a MP3.
```
ffmpeg -i input.webm -acodec libmp3lame -aq 4 output.mp3
```
First you may have to enable libmp3lame in ffmpeg (see option B):
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

