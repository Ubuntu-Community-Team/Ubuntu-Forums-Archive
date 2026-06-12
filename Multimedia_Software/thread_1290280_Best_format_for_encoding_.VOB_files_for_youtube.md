---
title: "Best format for encoding .VOB files for youtube?"
date: 2009-10-13
forum: Multimedia Software
---

### Post by sr_guy on 2009-10-13
I have a minidvd camcorder. I beleive each dvd is 1.2gig. I was wondering what the best format to use to encode the videos before uploading them to youtube. 

I have been using mecoder with the following examples. is there a better method that will produce better quality with Mencoder?

```

h263 =  mencoder test.vob -ovc lavc -lavcopts vcodec=h263:vbitrate=3500:abitrate=128 -vf scale=480:360 -oac copy -o test.mpg
mpg4 = mencoder test.vob -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=3500:abitrate=128 -vf scale=480:360 -oac copy -o test.mpg
h263p = mencoder test.vob -ovc lavc -lavcopts vcodec=h263p:vbitrate=3500:abitrate=128 -vf scale=480:360 -oac copy -o test.mpg


```

---

### Post by Nostalos on 2009-10-13
Why convert them at all as it is just going to be recoded to the proper format by youtube once the file is unloaded.  I think the requirements are less than 2GB and under 10mins long and support for .mpg.

rename the .vob file to .mpg as .vob is still an MPEG container file and upload it.   Google is going to recode the file once its uploaded anyway to h264 for flash playback.  


However if you are looking to recode it to make it smaller when uploaded you might try "-ovc x264" which will take alot longer but provide far better quality than mpg4 (divx quality) or h263 (RealVideo).  The drawback is that its way slower encoding.

---

### Post by sr_guy on 2009-10-13
Nostalos,

I tried as you suggested, using:

```

mencoder test.vob -ovc x264 -lavcopts vcodec=x264:vbitrate=3500:abitrate=128 -vf scale=480:360 -oac copy -o test.mpg

```

And get this error:

```

MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 28, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0x11ac729c
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  []  720x480  24bpp  29.970 fps  3691.0 kbps (450.6 kbyte/s)
[V] filefmt:3  fourcc:0x10000002  size:720x480  fps:29.97  ftime:=0.0334
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [scale w=704 h=480]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
audiocodec: framecopy (format=2000 chans=2 rate=48000 bits=16 B/s=32000 sample-1)
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
SwScaler: reducing / aligning filtersize 6 -> 8
SwScaler: reducing / aligning filtersize 6 -> 8
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 1 -> 1
[swscaler @ 0x883e3d0]SwScaler: BICUBIC scaler, from yuv420p to yuv420p using MMX2
[swscaler @ 0x883e3d0]SwScaler: using 8-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x883e3d0]SwScaler: using 8-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x883e3d0]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x883e3d0]SwScaler: 720x480 -> 704x480
x264 [error]: no ratecontrol method specified
x264_encoder_open failed.
FATAL: Cannot initialize video driver.

```

I believe all the necessary x264 packages are installed, so I'm not sure why I'm getting that error:

```


root@KG:/home/# dpkg --get-selections | grep x264
libx264-57                                      install
libx264-59                                      install
libx264-65                                      deinstall
libx264-dev                                     install
x264                                            install
root@KG:/home/#

```

Any further suggestions would be appreciated.

---

### Post by Nostalos on 2009-10-13
I'm no mencoder expert, but the single script i've used is just this.

```

mencoder input.avi -o output.avi -ovc x264 -x264encopts bitrate=3000 pass=1 nr=2000
```


I quit using mencoder sometime ago for the ease of Handbrake.

---

### Post by sr_guy on 2009-10-14
Nostalos,

Thanks. I hadn't heard of handbrake. Just installed it and took at his wiki. Works great. CLI interface too =)

---

### Post by Nostalos on 2009-10-14
Glad to Help.

---

### Post by vinutux on 2009-10-14
yeh...handbrake is very powerfull app....

---

