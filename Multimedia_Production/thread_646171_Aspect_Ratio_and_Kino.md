---
title: "Aspect Ratio and Kino"
date: 2007-12-20
forum: Multimedia Production
---

### Post by snaga on 2007-12-20
Just got a new JVC Everio MG155.  I like it so far...

I would like, or course, to do my video editing in Linux. I've tried most all of the video editors, and Kino seems to be the one that I like best, and it does what I need it to do.

I do have one problem thats a deal breaker, though. I'm hoping someone can help me.

I am recording on the Everio in 16:9, 720x480. When I import it into Kino, with my prefs set to 16:9, it does make a 16x9 frame, but the video itself is squished down to I think 4:3 in the middle, with vertical black bars on the sides. Is there any way to avoid this?

I have tried to use ffmpeg to convert the MOD file to a dv that Kino can open. This is what happens:

```
user@Pegasus:~/videos/ballet$ ffmpeg -i WBC_JC_parents_show_dec_2007_3.MOD -croptop 84 -cropbottom 84 -aspect 16:9 -deinterlace -target dv WBC_JC_parents_show_dec_2007_3.dv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mpeg, from 'WBC_JC_parents_show_dec_2007_3.MOD':
  Duration: 00:00:30.7, start: 0.199456, bitrate: 6610 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 8400 kb/s, 29.97 fps(r)
  Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, stereo, 384 kb/s
Assuming NTSC for target.
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, dv, to 'WBC_JC_parents_show_dec_2007_3.dv':
  Stream #0.0: Video: dvvideo, yuv411p, 720x480, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1

```

It looks like ffmpeg doesn't have the right codec, but I'm not sure where to get the right one. I have libavcodec installed.

Any thoughts? Using kino 1.1 and Gutsy.

---

### Post by ddennedy on 2007-12-23
ffmpeg is not able to read the audio stream in your source file. The reason Kino's import worked is because you have mplayer/mencoder and it does support the audio track format. Kino's script is using mencoder to decode to uncompressed and piping that into ffmpeg for encoding. The script does attempt to encode to widescreen. It only uses the aspect option from Preferences when your project is **empty**.

You can locate $prefix/share/kino/scripts/import/media.sh to see what is going on and maybe try to figure out the problem. Maybe mencoder is interpreting it as 4:3 and then padding it with the black.

---

### Post by sweetlou1 on 2007-12-23
actually i have no idea about all that.

---

### Post by billstei on 2008-01-17
Slightly off topic:

I take it you have no trouble with USB transfer from the JVC GZ-MG155 ?  Or are you using the Everio dock/firewire ?  Am thinking about getting this camera and want to make sure transfer works well in Linux.

Bill

---

### Post by zhkent on 2008-02-15
billstei,
The camera will appear as a removable hard drive.  The pictures and movies can be dragged and dropped onto the desktop, this part works great.
The problem is the movie file type which is .mod .
Rather difficult to get these files to work.  I would certainly check file type compatibility next time.

---

