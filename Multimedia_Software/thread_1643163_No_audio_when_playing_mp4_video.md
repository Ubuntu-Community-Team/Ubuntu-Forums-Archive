---
title: "No audio when playing mp4 video"
date: 2010-12-11
forum: Multimedia Software
---

### Post by ahaitoute on 2010-12-11
Hello,

I'm not getting audio when I play a video file.

```
mplayer Naruto/Naruto\ Shippuuden\ -\ 185 v2.mp4 
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Naruto/Naruto Shippuuden - 185.mp4.
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  848x480  24bpp  119.880 fps  1004.8 kbps (122.7 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 1
 compatible_brands: isom

Too many video packets in the buffer: (4096 in 14629387 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

Too many video packets in the buffer: (4096 in 14629387 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 848x480 => 848x480 Planar YV12 
A:   0.0 V:   0.0 A-V: -0.042 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Too many video packets in the buffer: (4096 in 14620782 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.1 A-V: -0.083 ct: -0.010   0/  0 ??% ??% ??,?% 0 0 
Too many video packets in the buffer: (4096 in 14607346 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.1 A-V: -0.125 ct: -0.025   0/  0 ??% ??% ??,?% 0 0 
Too many video packets in the buffer: (4096 in 14607066 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.2 A-V: -0.167 ct: -0.041   0/  0 ??% ??% ??,?% 0 0 

```
And so on....

The video file plays well with windows media player so I don't think its something wrong with the file. I've downloaded it from [http://www.takafansubs.com/](http://www.takafansubs.com/)

Is this a bug? Can someone help me fix this issue?

---

### Post by ron999 on 2010-12-11
Hi
I don't know why mPlayer won't play the sound.
But VLC plays the file OK with sound.

---

### Post by ahaitoute on 2010-12-11
This is weird...

Before I've submitted this thread I've tried to play it with VLC but I got only sound. But now after your suggestion I've tried it again and now it works! :D

Thanks!

---

