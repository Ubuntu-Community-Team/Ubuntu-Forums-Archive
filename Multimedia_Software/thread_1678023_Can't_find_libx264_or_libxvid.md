---
title: "Can't find libx264 or libxvid"
date: 2011-01-29
forum: Multimedia Software
---

### Post by hamstap85 on 2011-01-29
I'm using mencoder to encode a DVD on my computer (reading it is not an issue), and I'm having trouble getting the codec to read a certain library.

My command includes these options:
```
-ovc lavc
-lavcopts vcodec=libx264 (I also tried with libxvid)
```

It spat out this error at the end:
```
Cannot find codec 'libxvid' in libavcodec...
Couldn't open video filter 'lavc'.
Failed to open the encoder.

Exiting...
```

Unless I can get this working I'll fall back on mpeg4 but I would like these codecs. I've had good experiences with them. I've checked and the libx264-98 package is installed, along with libxvidcore4 and avifile-xvid-plugin

Is this a permission problem? Or do I have to set a conf file?

DO NOT suggest using a different -ovc or vcodec. If you have one that works for you, keep that for yourself. I am going to use lavc.

This isn't really life or death here. I'd just like it to be able to work!

---

### Post by BicyclerBoy on 2011-01-29
AFAIK this error is related to the stripped libavcodec, format

If you add medibuntu ppa (& load the key) in synaptic & then reload.

libavcodec format util etc should be replaced with unstripped "extra" packages.

You could also install w32-codecs or w64-codecs & libdvdcss.

Search ubuntu website for restricted formats & medibuntu for clear instructions.

---

### Post by hamstap85 on 2011-01-29
> **BicyclerBoy said:**
> AFAIK this error is related to the stripped libavcodec, format

If you add medibuntu ppa (& load the key) in synaptic & then reload.

libavcodec format util etc should be replaced with unstripped "extra" packages.

You could also install w32-codecs or w64-codecs & libdvdcss.

Search ubuntu website for restricted formats & medibuntu for clear instructions.
Now it gives me this:

```
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
videocodec: libavcodec (720x480 fourcc=34363268 [h264])
[VE_LAVC] High quality encoding selected (non-realtime)!
[libx264 @ 0x2144660]broken ffmpeg default settings detected
[libx264 @ 0x2144660]use an encoding preset (vpre)
Could not open codec.
FATAL: Cannot initialize video driver.
[mpeg2video @ 0x2144f90]ac-tex damaged at 22 7
[mpeg2video @ 0x2144f90]Warning MVs not available
[mpeg2video @ 0x2144f90]concealing 1035 DC, 1035 AC, 1035 MV errors

Exiting...
```

I even installed the dev packages of libx264 and libxvid

---

### Post by BicyclerBoy on 2011-01-29
It is strongly recommended to use presets with x264 (libx264) now.

The error is telling you the mencoder options for ffmpeg, you are using, are invalid now for x264.

Mencoder uses ffmpeg & w32-codecs w64-codecs & other stuff AFAIK.

I think mencoder is deprecated in favour of using mplayer directly.

There is loads of web info about mencoder x264 presets etc..

---

### Post by andrew.46 on 2011-02-27
A typical use of x264 presets with MEncoder could be:

```
-ovc x264 -x264encopts preset=slow:tune=film:crf=22
```

Andrew

---

