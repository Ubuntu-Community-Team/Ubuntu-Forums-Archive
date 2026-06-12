---
title: "Help with ffmpeg reducing video quality in output"
date: 2011-04-26
forum: Multimedia Software
---

### Post by kelt65 on 2011-04-26
I'm trying to use ffmpeg to strip the audio from some video files. However, it is reducing the bitrate of the resulting video tremendously.

Is there a way to get ffmpeg to simply keep the original video settings?

Barring that, I've tried like so:
```
ffmpeg -i inputfile.avi -b 1286 -an outputfile.avi
```

The inputfile has a bitrate of 1286kbs. But this command results in a video with a bitrate of 248kbs (and it looks horrible). Why is ffmpeg ignoring the "-b" switch here? There's nothing in the output that indicates any error. Here it is:
```

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (959/40)
Input #0, avi, from 'inputfile.avi':
  Duration: 00:00:04.58, start: 0.000000, bitrate: 1286 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 512x384 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 112 kb/s
File 'outputfile.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to 'outputfile.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 512x384 [PAR 1:1 DAR 4:3], q=2-31, 1 kb/s, 23.98 tbn, 23.98 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=  110 fps=  0 q=31.0 Lsize=     136kB time=4.59 bitrate= 242.4kbits/s    
video:128kB audio:0kB global headers:0kB muxing overhead 6.478170%

```

How can I get this to work?

Is there any other program that can easily remove audio from video clips? If I recall correctly, avidemux used to have a "none" audio target that would do the same thing, but I don't see it there any more.

---

### Post by ron999 on 2011-04-26
Hi
Try this command instead:-
```
ffmpeg -i inputfile.avi -vcodec copy -an outputfile.avi
```

---

### Post by kelt65 on 2011-04-26
> **ron999 said:**
> Hi
Try this command instead:-
```
ffmpeg -i inputfile.avi -vcodec copy -an outputfile.avi
```

THANK YOU! Just what I wanted. I swear I read the man page until my eyes glazed over, but I seemed to have missed that ...

---

