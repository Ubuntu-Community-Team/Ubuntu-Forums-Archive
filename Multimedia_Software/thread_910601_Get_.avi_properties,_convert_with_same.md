---
title: "Get .avi properties, convert with same"
date: 2008-09-04
forum: Multimedia Software
---

### Post by WildgOphers on 2008-09-04
What I'm trying to do is get the file type and info from a video file (AVI) and use that as a template to convert new file to that exact same type so I can put it on a mobile device. The info I have so far is:

```
[tcprobe] RIFF data, AVI video
[avilib] V: 20.000 fps, codec=XVID, frames=599, width=320, height=240
[avilib] A: 44100 Hz, format=0x50, bits=0, channels=2, bitrate=128 kbps,
[avilib]    1152 chunks, 481534 bytes, VBR
[tcprobe] summary for /home/brenden/Desktop/latte.avi, (*) = not default, 0 = not detected
import frame size: -g 320x240 [720x576] (*)
       frame rate: -f 20.000 [25.000] frc=0 (*)
      audio track: -a 0 [0] -e 44100,0,2 [48000,16,2] -n 0x50 [0x2000] (*)
                   bitrate=128 kbps
           length: 599 frames, frame_time=50 msec, duration=0:00:29.950


RIFF (little-endian) data, AVI, 320 x 240, 20.00 fps, video: XviD, audio: MPEG-1 Layer 1 or 2 (stereo, 44100 Hz)
```

So the info I have so far is:

AVI
20 fps
XVID MPEG-4
320x240
44100 Hz
128 kbps
MPEG-1 Layer 2 (mp2)

But when I convert to these specs in Avidemux It's not playing on the mobile device (mp3 player). I'm not sure if I'm missing something from the .avi file or if something is getting lost in conversion.

So my questions are:

A)Do I need some more info from the .avi file, am I missing something?
B)Can I convert properly in Avidemux? (or mencoder, but wading through that man file looks damn near impossible.)

---

