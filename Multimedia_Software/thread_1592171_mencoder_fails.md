---
title: "mencoder fails"
date: 2010-10-10
forum: Multimedia Software
---

### Post by mstjohn1974 on 2010-10-10
I am trying to convert a clip I recorded with recordmydesktop and it fails and I dont understand why. I copy the output below. Maybe someone here knows wat the heck is going on. 

The input video formats are:
Dimensions: 1280x736
Codec: Theora
Framerate:25

and Audio is:
Codec: Vorbis
Channel: Mono
Sample Rate: 44100hz
Bitrate: 239

And I like to get the video to be 1280x720 with 25fps in divx/xvid and the audio to be mp3 with 128kbps bitrate and 44100hz sample rate.


Thanks

mencoder -srate 48000 -af lavcresample=48000 -noautosub -oac mp3lame -aid 0 -ovc lavc -ofps 25000/1001 -ffourcc DX50 -vf expand=1280:960:0:112,scale=1280:720 -lavcopts threads=2:vcodec=mpeg4:trell:mbd=2:sc_threshold=1000000000:cgop:vbitrate=1001:aspect=4/3 -lameopts abr:br=128 -o /home/msj/movie/movie_01_01.avi /home/msj/Videos/out-1.ogv
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x93104ac
libavformat file format detected.
[ogg @ 0x977cb00]max_analyze_duration reached
[lavf] stream 1: video (theora), -vid 0
[lavf] stream 2: audio (vorbis), -aid 0
VIDEO:  [theo]  1280x736  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x6F656874  size:1280x736  fps:25.000  ftime:=0.0400
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 239.9 kbit/34.00% (ratio: 29990->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=1280 h=720]
Opening video filter: [expand w=1280 h=960 x=0 y=112]
Expand: 1280 x 960, 0 ; 112, osd: 0, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [fftheora] vfm: ffmpeg (FFmpeg Theora)
==========================================================================
Forcing output FourCC to 30355844 [DX50].
MP3 audio selected.
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
[swscaler @ 0x9be0e60]BICUBIC scaler, from yuv420p to yuv420p using MMX2
videocodec: libavcodec (1280x720 fourcc=30355844 [DX50])
[VE_LAVC] High quality encoding selected (non-realtime)!
Full DR not possible, trying SLICES instead!
Segmentation fault

---

### Post by ron999 on 2010-10-10
Hi
Test mencoder with a simple command first.
Like this:-
```
mencoder /home/msj/Videos/out-1.ogv -o /home/msj/movie/movie_01_01.avi -ovc lavc -oac mp3lame
```

---

### Post by mstjohn1974 on 2010-10-10
this one return the following:

MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x93104ac
libavformat file format detected.
[ogg @ 0x88d9500]max_analyze_duration reached
[lavf] stream 1: video (theora), -vid 0
[lavf] stream 2: audio (vorbis), -aid 0
VIDEO:  [theo]  1280x736  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:44  fourcc:0x6F656874  size:1280x736  fps:25.000  ftime:=0.0400
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 239.9 kbit/34.00% (ratio: 29990->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [fftheora] vfm: ffmpeg (FFmpeg Theora)
==========================================================================
MP3 audio selected.
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
videocodec: libavcodec (1280x736 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
[VD_FFMPEG] DRI failure.)  0.00fps Trem:   0min   4mb  A-V:0.004 [0:0]
Pos:   1.6s     41f ( 0%)  0.00fps Trem:   0min   9mb  A-V:-0.082 [280:100]
1 duplicate frame(s)!
Pos:   2.1s     51f ( 0%)  0.00fps Trem:   0min  10mb  A-V:-0.082 [241:100]
1 duplicate frame(s)!
Pos:   2.5s     61f ( 0%)  0.00fps Trem:   1min  11mb  A-V:-0.082 [217:100]
1 duplicate frame(s)!
Pos:   3.0s     71f ( 0%)  0.00fps Trem:   1min  13mb  A-V:-0.082 [200:101]
1 duplicate frame(s)!
Pos:   3.4s     81f ( 0%)  0.00fps Trem:   1min  14mb  A-V:-0.082 [186:103]
1 duplicate frame(s)!
Pos:   3.8s     91f ( 0%)  0.00fps Trem:   1min  15mb  A-V:-0.082 [176:104]
1 duplicate frame(s)!
Pos:   4.3s    101f ( 0%) 99.02fps Trem:   1min  16mb  A-V:-0.082 [168:105]
1 duplicate frame(s)!
Pos:   4.7s    111f ( 0%) 99.37fps Trem:   2min  18mb  A-V:-0.082 [162:105]
1 duplicate frame(s)!
Pos:   5.2s    121f ( 0%) 99.67fps Trem:   2min  19mb  A-V:-0.082 [157:106]
1 duplicate frame(s)!
Pos:   5.6s    131f ( 0%) 100.00fps Trem:   2min  20mb  A-V:-0.082 [152:106]
1 duplicate frame(s)!
Pos:   6.0s    141f ( 0%) 100.28fps Trem:   2min  20mb  A-V:-0.082 [148:107]
1 duplicate frame(s)!
Pos:   6.5s    151f ( 1%) 100.47fps Trem:   2min  20mb  A-V:-0.082 [145:107]
1 duplicate frame(s)!
Pos:   6.9s    161f ( 1%) 100.50fps Trem:   2min  20mb  A-V:-0.082 [142:108]
1 duplicate frame(s)!
Pos:   7.4s    171f ( 1%) 100.59fps Trem:   2min  20mb  A-V:-0.082 [140:107]
1 duplicate frame(s)!
Pos:   7.8s    181f ( 1%) 100.78fps Trem:   2min  20mb  A-V:-0.082 [137:108]
1 duplicate frame(s)!
Pos:   8.0s    184f ( 1%) 100.66fps Trem:   2min  20mb  A-V:-0.054 [136:108]
Too many audio packets in the buffer: (4096 in 962172 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  136.736 kbit/s  (17091 B/s)  size: 136052 bytes  7.960 secs  184 frames

Audio stream:  108.482 kbit/s  (13560 B/s)  size: 114770 bytes  8.464 secs

---

### Post by SeijiSensei on 2010-10-11
First, see if mplayer will play the original file.  Run it from the command line using "mplayer /path/to/video/file" and see what it reports.

Rather than using lavc, you could try the xvid codec in mencoder like this:

```
mencoder -o output.avi -oac mp3lame -lameopts vbr=3 -ovc xvid -xvidencopts=pass=1 input.ogv
```

---

