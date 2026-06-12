---
title: "avidemux: no audio decoder for audio (mu-law format)"
date: 2011-05-29
forum: Multimedia Software
---

### Post by halbbitter on 2011-05-29
I have some AVI video files, filmed with the Kodak camera. They use "mu-law" format for audio. I would like to edit this file and save it to another format (xvid/mp3).

When I try to open such file with Avidemux, I get error: "No audio decoder found for this file".

What can I do about this? 
My system is 11.04, avidemux version is 2.5.4

---

### Post by andrew.46 on 2011-05-30
Perhaps see if your copy of FFmpeg supports this:

```

andrew@skamandros~$**[COLOR="Red"] ffmpeg -codecs | grep mulaw[/COLOR]**
ffmpeg version git-N-30341-g8381ab1, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 28 2011 09:38:44 with gcc 4.5.3
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-amrwbenc --enable-libvo-aacenc --enable-libfreetype --enable-nonfree --enable-gpl --enable-version3
  libavutil    51.  2. 2 / 51.  2. 2
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  2. 0 / 53.  2. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2. 11. 0 /  2. 11. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
**[COLOR="Red"] DEA    pcm_mulaw       PCM mu-law[/COLOR]**

```

If so encoding to another format should be pretty straightforward.

---

### Post by halbbitter on 2011-06-05
Thanks! Not surprisingly, my output of 'ffmpeg -codecs' is exactly the same.

Anyway, I was able to transcode my files using Pitivi (which I suppose uses ffmpeg under the hood). Problem resolved.

---

### Post by andrew.46 on 2011-06-07
> **halbbitter said:**
> Thanks! Not surprisingly, my output of 'ffmpeg -codecs' is exactly the same.

You would be surprised, there are many different versions of FFmpeg around with vastly different capabilities and I confess that I am not using the repository version. Anyway great to hear that you have solved your problem :).

---

