---
title: "Input buffer exhausted before END element found"
date: 2010-06-13
forum: Multimedia Software
---

### Post by luofeiyu on 2010-06-13
ffmpeg  -i /home/v.mp4  -sameq  /home/v.mpg

FFmpeg version SVN-r23596, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 13 2010 08:49:47 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.76. 0 / 52.76. 0
  libavformat   52.68. 0 / 52.68. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/v.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isom
  Duration: 00:05:49.09, start: 0.000000, bitrate: 399 kb/s
    Stream #0.0(chi): Video: h264, yuv420p, 576x432 [PAR 1:1 DAR 4:3], 380 kb/s, 25 fps, 25 tbr, 25 tbn, 50 tbc
    Stream #0.1(chi): Audio: aac, 48000 Hz, mono, s16, 16 kb/s
Output #0, mpeg, to '/home/v.mpg':
  Metadata:
    encoder         : Lavf52.68.0
    Stream #0.0(chi): Video: mpeg1video, yuv420p, 576x432 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1(chi): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[mpeg1video @ 0xa72c010]warning, clipping 1 dct coefficients to -255..255
    Last message repeated 63 times94750kB time=346.70 bitrate=2238.8kbits/s    
[aac @ 0xa72a130]Input buffer exhausted before END element found
Error while decoding stream #0.1
frame= 8723 fps=109 q=0.0 Lsize=   95312kB time=348.77 bitrate=2238.7kbits/s    
video:92069kB audio:2725kB global headers:0kB muxing overhead 0.546604%
how  to  fix  it?

---

### Post by luofeiyu on 2010-06-13
pt@pt-laptop:~$ ffmpeg  -i /home/vcd.mp4    /home/vcd.mpg
FFmpeg version SVN-r23596, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 13 2010 08:49:47 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.76. 0 / 52.76. 0
  libavformat   52.68. 0 / 52.68. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[flv @ 0x9136510]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from '/home/vcd.mp4':
  Metadata:
    metadatacreator : Yet Another Metadata Injector for FLV - Version 1.4
    hasKeyframes    : true
    hasVideo        : true
    hasAudio        : true
    hasMetadata     : true
    canSeekToEnd    : false
    duration        : 422
    datasize        : 13371348
    videosize       : 10252554
    videocodecid    : 2
    width           : 320
    height          : 218
    framerate       : 15
    videodatarate   : 189
    audiosize       : 3028842
    audiocodecid    : 2
    audiosamplerate : 22000
    audiosamplesize : 16
    stereo          : true
    audiodatarate   : 53
    filesize        : 13373401
    lasttimestamp   : 422
    lastkeyframetimestamp: 416
    lastkeyframelocation: 13182835
  Duration: 00:07:02.00, start: 0.000000, bitrate: 249 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x218, 193 kb/s, 15 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 2 channels, s16, 56 kb/s
[mpeg1video @ 0x913b6d0]MPEG1/2 does not support 15/1 fps
Output #0, mpeg, to '/home/vcd.mpg':
    Stream #0.0: Video: mpeg1video, yuv420p, 320x218, q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: mp2, 22050 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

how to fix  it?

---

### Post by luofeiyu on 2010-06-13
pt@pt-laptop:~$ mencoder  /home/vcd.mp4   -ovc lavc    -oac lavc -o /home/vcd.mpg
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xcc0fda
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x218  0bpp  15.000 fps  193.0 kbps (23.6 kbyte/s)
[V] filefmt:44  fourcc:0x31564C46  size:320x218  fps:15.000  ftime:=0.0667
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 56.0 kbit/7.94% (ratio: 7000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
[mp2 @ 0x9c61fd0]bitrate 224 is not allowed in mp2
Couldn't open codec mp2, br=224.

Exiting...
pt@pt-laptop:~$

---

### Post by fernando.gottlieb on 2011-06-23
You can avoid this boring message determining the audio bitrate like this:

-lavcopts abitrate=160

Like this code:

mencoder /home/vcd.mp4 -ovc lavc -oac lavc -lavcopts abitrate=160 -o /home/vcd.mpg

PS: this solution i´ve found at another thread (Convert .ogg to mpeg using mencoder? - 456962) at UbuntuForums.org too! 

May this will help you like helped me! Thanks for the author JeevesBond!

Best regards.

Fernando A. Gottlieb

---

