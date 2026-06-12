---
title: "xubuntu 12.10 ffmpeg unknown encoder libvpx"
date: 2013-01-14
forum: Multimedia Software
---

### Post by vectorthorn on 2013-01-14
```

$ ffmpeg -i 01.mkv -vf scale=0.5 -vcodec -libvpx -vb 1024k -acodec libvorbis -aq 3 -ac 1 01.webm
ffmpeg version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:11 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x1761ba0] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '01.mkv':
  Duration: 00:08:51.80, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 1920x1200 [PAR 1:1 DAR 8:5], 20 fps, 20 tbr, 1k tbn, 20 tbc (default)
    Stream #0.1: Audio: vorbis, 48000 Hz, stereo, s16 (default)
** Unknown encoder '-libvpx'**
$ 
$ 
$ 
$ avconv -i 01.mkv -vf scale=0.5 -vcodec -libvpx -vb 1024k -acodec libvorbis -aq 3 -ac 1 01.webm
avconv version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:11 with gcc 4.7.2
[matroska,webm @ 0xd3cb80] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '01.mkv':
  Duration: 00:08:51.80, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 1920x1200 [PAR 1:1 DAR 8:5], 20 fps, 20 tbr, 1k tbn, 20 tbc (default)
    Stream #0.1: Audio: vorbis, 48000 Hz, stereo, s16 (default)
** Unknown encoder '-libvpx'**
$ 
$ 
$ 
$ ffmpeg -codecs
...
 D V D  vp8             On2 VP8
...
$ 
$ 
$ 
$ avconv -codecs
...
 D V D  vp8             On2 VP8
...

```and  i installed the gstreamer [good, bad, ugly, ffmpeg] as well as a lot of  other multimedia plugins, including the extras-53 plugins. was not  having this problem in 12.04 [o_O]

TIA

---

### Post by ron999 on 2013-01-14
Unknown encoder '-libvpx'

Doh, remove the minus sign from in front of libvpx!

---

### Post by ajgreeny on 2013-01-14
Have you installed libvpx0?  It is in the 10.04 repos and will presumably be in all others as well.

However, if you have not compiled ffmpeg yourself, you should now be using the command **avconv** which is in the libav-tools package instead in 12.10.
[http://libav.org/](http://libav.org/)
[https://help.ubuntu.com/community/FFmpeg](https://help.ubuntu.com/community/FFmpeg)

---

### Post by vectorthorn on 2013-01-14
> **ron999 said:**
> Unknown encoder '-libvpx'

Doh, remove the minus sign from in front of libvpx!
... as long as i've been doing this ... and i didn't even catch that ... [-_-]
i even wrote the multimedia system behind [http://eevvee.com](http://eevvee.com) ...  [-_-]
thanks
\m/ (>_<) \m/

---

