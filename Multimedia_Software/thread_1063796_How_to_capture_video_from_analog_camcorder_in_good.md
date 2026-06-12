---
title: "How to capture video from analog camcorder in good quality?"
date: 2009-02-08
forum: Multimedia Software
---

### Post by stando007 on 2009-02-08
Hi,

I have Ubuntu 8.10, Dell Optiplex GX620 PC with 3GHz P4 CPU, 2.5GB DDR2. I think this HW config should be enough for capturing video in some good quality.

I want to grab my video collection from analog Hi8 camcorder. Camcorder has S-video and video composite output. I have AverMedia TV Phone 98 card.
My TV card is capable to capturing video - I tried it with this:

mencoder tv:// -tv input=2 -o movie.avi -nosound -ovc lavc -lavcopts vcodec=mpeg4

I was able to capture video from input=2, which is S-video on my TV card. I did not experimented with audio till now, I need to get acceptable results with video first. Everything is fine, but video is  a bit jerky, interlaced (visible image distortion with horizontal lines while moving), moving is not smooth. I think I am doing something wrong. Should I first capture onlu uncompressed video and then make some transcoding for getting good quality???

Sample output of the mencoder:
```
xxx@xxx-desktop:~$ mencoder tv:// -tv input=2 -o movie.avi -nosound -ovc lavc -lavcopts vcodec=mpeg4
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: BT878 video (AVerMedia TVPhone 
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  video overlay  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = PAL; 5 = PAL-BG; 6 = PAL-H; 7 = PAL-I; 8 = PAL-DK; 9 = PAL-M; 10 = PAL-N; 11 = PAL-Nc; 12 = PAL-60; 13 = SECAM; 14 = SECAM-B; 15 = SECAM-G; 16 = SECAM-H; 17 = SECAM-DK; 18 = SECAM-L; 19 = SECAM-Lc;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 2
 Current format: YVU420
v4l2: current audio mode is : LANG1
[V] filefmt:9  fourcc:0x32315659  size:640x480  fps:25.00  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (640x480 fourcc=34504d46 [FMP4])
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Forcing audio preload to 0, max pts correction to 0.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
^CPos:   9.9s    247f ( 0%) 24.73fps Trem:   0min   0mb  A-V:0.000 [34:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:   34.002 kbit/s  (4250 B/s)  size: 41993 bytes  9.880 secs  247 frames
v4l2: 249 frames successfully processed, 0 frames dropped.

```

[B]Could somebody give me some practical advises which software to use, which steps needed to be made, which configurations, and which codecs....? 
[/B]
I want to get some normal quality videos which I am able to record on DVD-R for DVD player or to use some xvid/divx codec also for playing on some home AV player.
The quality of Hi8 analog tapes is not extremely good, bud I would like to remain in some similar quality even on digital media.

---

### Post by punx45 on 2009-02-08
rule of thumb is always start with the highest quality you can.   MPEG2 is still compressed, but it is pretty high quality, so that could be a good place to start.   the interlacing is normal. it always looks bad on computer screens.

also it looked like from that output you gave that it encoded at 25fps.   are you in europe?   is it a PAL camcorder?

if you are in the US it should be 30fps (29.97 technically, but i dont know how mencoder handles that).   that may have contributed to the choppiness.   also, NTSC video (if  you are in the US) is 720x486, where that encoded at 640x480, so you can bump that up too.

---

### Post by stando007 on 2009-02-08
I am in Europe, camcorder is PAL. That is also I would need to know - at what FPS should I encode. Is that 25 FPS ok for PAL? How can I control FPS of the encoding?
And is mencoder the right tool for it?
Every information is really needful because I am complete newbie to grabbing, encoding and I use Ubuntu as my "secondary" OS and quite like it.

So what should I do? Capture directly to MPEG2 without any filters like deinterlace or some other filter? And later to transcode and correct?

Please I would be very happy if somebody gives me short and clear howto for newbie :)

---

### Post by punx45 on 2009-02-08
yeah, PAL is 25fps.   capture the source in its natural state, no filters, etc.  then process from that for your intended format.   i dont know much about PAL but if interlacing works the same as it does in NTSC, leave it as it is for DVDs and you can deinterlace video that is intended to be watched on a PC.

unfortuantely i cant get more specific as i am not terribly experienced with linux video tools.

---

### Post by stando007 on 2009-02-08
I tried to capture direct into mpeg4 before. I set to higher bitrate, so captured video was quite fine quality, but of course there was interlacing visible while playing on PC. But I tried to copy that avi file to USB flash and plugged into my DVD player and played it - there was heavy interlacing visible, watching such video was almost impossible. So I think I need some deinterlacing or I do "something" wrong.

---

### Post by punx45 on 2009-02-08
yeah try deinterlacing it then i guess.   i more meant if you were burning it to a DVD as a standard playable DVD, then keep the interlacing.

---

### Post by stando007 on 2009-02-08
OK, thanks for advices! I will try and will back here if there are some problems. I did not try to record audio till now, so hope it will not be a problem.

In windows I tried software iuVCR before, it was really intuitive and simple, but it often crash (maybe drivers for my tv card under windows were not good). Here in Linux I can found it more robust, but it is a bit harder to learn all the usage of software's commands and to learn what communicates with what and in how conditions....

---

