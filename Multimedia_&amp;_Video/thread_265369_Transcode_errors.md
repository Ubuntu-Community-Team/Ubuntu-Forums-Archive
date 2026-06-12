---
title: "Transcode errors"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by dbbolton on 2006-09-25
i have been getting many errors using transcode when trying to output with ffmpeg, mped1enc, etc.; such as  ```
 [transcode] warning : no option -x found, option -i ignored, reading from "/dev/zero" [transcode] warning : (encoder.c) video export module error: init failed [transcode] critical: plug-in initialization failed [transcode] critical: failed to init encoder 
```  here is my result when i run probe: ```
 tcprobe -i /home/daniel/music_videos.avi [tcprobe] RIFF data, AVI video [avilib] V: 29.970 fps, codec=FMP4, frames=9023, width=480, height=360 [avilib] A: 48000 Hz, format=0x55, bits=0, channels=2, bitrate=127 kbps, [avilib]    12547 chunks, 4815216 bytes, VBR [tcprobe] summary for /home/daniel/music_videos.avi, (*) = not default, 0 = not detected import frame size: -g 480x360 [720x576] (*)        frame rate: -f 29.970 [25.000] frc=4 (*)       audio track: -a 0 [0] -e 48000,0,2 [48000,16,2] -n 0x55 [0x2000] (*)                    bitrate=127 kbps            length: 9023 frames, frame_time=33 msec, duration=0:05:01.067 
```  i would like to be able to save this as a smaller mpeg file. any thoughts?

---

### Post by Ikitt on 2006-09-27
Looks like a command line problem. Please post commandline used and full transcode reply.

---

### Post by dbbolton on 2006-11-13
thanks man, but i kinda gave up on that whole hornets nest and (much to my shame) used xp.

---

