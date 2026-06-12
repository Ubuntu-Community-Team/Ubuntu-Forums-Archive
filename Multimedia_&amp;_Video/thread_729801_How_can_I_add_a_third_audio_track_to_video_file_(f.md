---
title: "How can I add a third audio track to video file (ffmeg, transcoder)?"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by Tharmas on 2008-03-20
Is it possible?

I have a .avi file with 1 video (xvid) and 2 audio (mp3) streams. I want to add a 3rd audio stream.

I tried **avidemux2**, but it only allows 2 audio streams per file.

I tried **ffmpeg** using:

```
ffmpeg -i input.avi -i 3rd_audio.mp3 -vcodec copy -acodec copy output.avi -newaudio
```

and I get:

```

Input #0, avi, from 'input.avi':
  Duration: 127:06:55.8, start: 0.000000, bitrate: 7 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 720x400, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 96 kb/s
  Stream #0.2: Audio: mp2, 48000 Hz, mono, 64 kb/s
Input #1, mp3, from '3rd_audio.mp3':
  Duration: 00:20:00.5, start: 0.000000, bitrate: 128 kb/s
  Stream #1.0: Audio: mp3, 48000 Hz, mono, 128 kb/s
Output #0, avi, to 'output.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 720x400, q=2-31, 25.00 fps(c)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 96 kb/s
  Stream #0.2: Audio: mp2, 48000 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.2 -> #0.2
```

So it seams ffmpeg does ignores the 3r audio stream, and it worked when I added the 2nd.

Trying to specify the mapping  ```
ffmpeg -i input.avi -i 3rd_audio.mp3 -map 0:0 -map 0:1 -map 0:2 -map 1:0 -vcodec copy -acodec copy output.avi -newaudio
``` also didn't work, as it complained "Number of stream maps must match number of output streams"

Is it possible to acomplish this in linux with ffmpeg or any other available tool?

---

