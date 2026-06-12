---
title: "FFmpeg &quot;Unsupported Codec for Stream #0.3&quot;"
date: 2010-06-30
forum: Multimedia Software
---

### Post by Zerocool3001 on 2010-06-30
I've been trying to re-mux some mkv files into mp4 files recently and ran into this issue. The mkv files contain an h.264 video stream, two aac audio streams (english and japanese) and one subtitle stream. All I'm trying to do is move all four streams into a mp4 container using the following command:

```
ffmpeg -i input.mkv -vcodec copy -acodec copy -acodec copy -scodec copy output.m4v -newaudio

```
```
Input #0, matroska, from 'input.mkv':
  Duration: 00:24:42.64, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 640x480, PAR 1:1 DAR 4:3, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(jpn): Audio: aac, 11025 Hz, stereo, s16
    Stream #0.2(eng): Audio: aac, 24000 Hz, stereo, s16
    Stream #0.3(eng): Subtitle: 0x0000
File 'output.m4v' already exists. Overwrite ? [y/N] y
Output #0, ipod, to 'output.m4v':
    Stream #0.0: Video: libx264, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 90k tbn, 23.98 tbc
    Stream #0.1(jpn): Audio: 0x0000, 11025 Hz, stereo, s16
    Stream #0.2(eng): Subtitle: 0x0000
    Stream #0.3(eng): Audio: 0x0000, 24000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.3 -> #0.2
  Stream #0.2 -> #0.3
Unsupported codec for output stream #0.3

```

Since the first audio stream doesn't seem to be throwing an error I'm a little confused as to why the second (with the same codec) would give this error.

I would appreciate any help with this problem, or alternative solutions to accomplishing the mux.

---

### Post by ron999 on 2010-06-30
Hi
Try using **mkvextract** to extract the 4 streams.
It's part of the package **mkvtoolnix**.
Then pack the 4 streams into an mp4 wrapper using **MP4Box**.
It's part of the package **gpac**.

To extract the streams the command is like this:-
```
mkvextract tracks input.mkv 1:video 2:audio1 3:audio2 4:subs

```
To pack the streams the command is like this:-
```
MP4Box -add video -add audio1 -add audio2 -add subs output.m4v
```

---

### Post by Zerocool3001 on 2010-06-30
I would really have liked to use ffmpeg for this, but it looks like the problem I ran into is a known bug with -acodec copy.

Your solution did produce mp4 files with the streams in them (I even threw together a quick bash script for batch processing!) but unfortunately it looks like the timing with the video stream was stripped when extracting. Once I put the files in an mp4 with MP4Box, both of the audio streams were out of sync.

I'm not really sure about the best way to solve this. Since I have 26 files it would be a pain to adjust the time by hand (assuming it is simply offset by a fixed amount). If anybody has any suggestions I'd appreciate it.

Thanks for your help ron999.

---

