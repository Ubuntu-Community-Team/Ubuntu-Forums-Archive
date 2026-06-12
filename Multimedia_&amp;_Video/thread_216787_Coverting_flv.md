---
title: "Coverting flv"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by Quicksilver_Johny on 2006-07-16
When running 
```
ffmpeg -i test.flv -ab 56 -ar 22050 -b 500 s 320x240 test.mpg
```
[flv @ 0x82c8200]Unsupported video codec (4)
[flv @ 0x82c8200]Unsupported video codec (4)
[flv @ 0x82c8200]Unsupported video codec (4)
[flv @ 0x82c8200]Unsupported video codec (4)
[flv @ 0x82c8200]Unsupported video codec (4)
[flv @ 0x82c8200]Unsupported video codec (4)
...
[flv @ 0x82c8200]Unsupported video codec (4)
[flv @ 0x82c8200]Unsupported video codec (4)
Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, flv, from 'test.flv':
  Duration: 00:23:55.4, bitrate: N/A
  Stream #0.0: Audio: mp3, 44100 Hz, stereo
  Stream #0.1: Video: 0x0004
Output #0, mpeg, to 'test.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 320x240, 24.00 fps, q=2-31, 500 kb/s
  Stream #0.1: Audio: mp2, 22050 Hz, stereo, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1

Do I need to install anything other than ffmpeg to get it to work?

Also, Playing Flv files in Mplayer:
...
[mpeg4 @ 0x86fd3e8]header damaged -0.004 4255/4255  0%  0%  2.2% 11 0
Error while decoding frame!
[flv @ 0x85f5200]Unsupported video codec (4)6/4256  0%  0%  2.2% 11 0
[mpeg4 @ 0x86fd3e8]header damaged
Error while decoding frame!
[flv @ 0x85f5200]Unsupported video codec (4)7/4257  0%  0%  2.2% 11 0
[flv @ 0x85f5200]Unsupported video codec (4)
[mpeg4 @ 0x86fd3e8]header damaged
Error while decoding frame!
...
It plays the sound, but not the video.



I'm Running Xubuntu.

---

### Post by Quicksilver_Johny on 2006-07-16
Anything? I don't really *need* to convert them, any way to play them. Hopefully, video and audio, but even just video is fine.

---

### Post by whatever on 2006-07-16
you can only play/reencode flv files which use the h263 codec.
those "flash 8 required"-movies use the vp6 codec and are not (yet) supported bei mplayer/mencoder.

---

### Post by Quicksilver_Johny on 2006-07-16
> **whatever said:**
> you can only play/reencode flv files which use the h263 codec.
those "flash 8 required"-movies use the vp6 codec and are not (yet) supported bei mplayer/mencoder.

-/ That's what I was afraid of. *Sigh* I don't know why people use flash...

---

