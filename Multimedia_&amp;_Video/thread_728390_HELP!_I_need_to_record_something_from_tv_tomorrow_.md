---
title: "HELP! I need to record something from tv tomorrow an mencoder is not giving me sound"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by slack31337 on 2008-03-18
i am recording using 

mencoder tv:// -tv driver=v4l2:norm=NTSC:chanlist=us-cable:channel=20:amode=1:device=/dev/video0 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1600 -oac mp3lame -lameopts cbr:br=128:mode=3 -vf crop=635:470:0:0 -endpos 10 -o test2a.avi

and for some reason it doesn't throw any errors and the video is great 


here is the output

MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Duron(tm)           (Family: 6, Model: 7, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: ASUS TV-FM 7135
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO STEREO
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL; 1 = PAL-BG; 2 = PAL-I; 3 = PAL-DK; 4 = NTSC; 5 = SECAM; 6 = SECAM-DK; 7 = SECAM-L; 8 = SECAM-Lc; 9 = PAL-M; 10 = PAL-Nc; 11 = PAL-60;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : STEREO
Selected channel: 20 (freq: 157.250)
Audio block size too low, setting to 16384!
[V] filefmt:9  fourcc:0x32315659  size:640x480  fps:29.97  ftime:=0.0334
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 1411.2 kbit/100.00% (ratio: 176400->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [crop w=635 h=470 x=0 y=0]
Crop: 635 x 470, 0 ; 0
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (635x470 fourcc=34504d46 [FMP4])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
MP3 audio selected.
Forcing audio preload to 0, max pts correction to 0.
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos:   0.1s      2f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
1 duplicate frame(s)!
Pos:  10.0s    299f ( 0%) 29.43fps Trem:   0min   0mb  A-V:0.000 [1721:127]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1721.531 kbit/s  (215191 B/s)  size: 2154066 bytes  10.010 secs  299 frames

Audio stream:  128.000 kbit/s  (15999 B/s)  size: 159660 bytes  9.979 secs
v4l2: 304 frames successfully processed, 0 frames dropped.

i end up with a 10 second video w/ no sound 

i have even tried 

mencoder tv:// -tv driver=v4l2:norm=NTSC:chanlist=us-cable:channel=20:amode=1:device=/dev/video0 -ovc lavc  -oac lavc  -endpos 10 -o test2short.avi


thanks for any help

---

### Post by xzero1 on 2008-03-19
When I record from my capture card the sound comes via the sound card (default) not the capture card. You may be capturing sound from the wrong source.

---

### Post by slack31337 on 2008-03-19
and how would i know if that is my case ?

---

### Post by xzero1 on 2008-03-20
You can attach an audio source into your soundcard's aux input and record as before. If you get sound, then try connecting the tv card sound output to aux. 
If you require sound directly from the card then these links may be of help:
[http://www.mplayerhq.hu/DOCS/HTML/en/tv-input.html]("http://www.mplayerhq.hu/DOCS/HTML/en/tv-input.html") 
[http://linuxtv.org/v4lwiki/index.php/Main_Page]("http://linuxtv.org/v4lwiki/index.php/Main_Page")
I think the mencoders adevice parameter will specify your sound input source.

---

