---
title: "convert mp4 to avi same quality ffmpeg?"
date: 2012-12-19
forum: Multimedia Software
---

### Post by sohlinux on 2012-12-19
How can I convert an mp4 video to an avi with the same quality, same bitrate, same codec, same audio quality, same screen resolution with ffmpeg from the command line?

I tried to convert a 100mb mp4 file with the following command

ffmpeg -i in.mp4 out.avi and the result is an avi file of 30mb so obviously the quality has degraded?

---

### Post by andrew.46 on 2012-12-19
Depends what is in your mp4 :). Can you show the full terminal output from just:

```
ffmpeg -i in.mp4
```

Any special reason for the avi container?

---

### Post by sohlinux on 2012-12-19
> **andrew.46 said:**
> Depends what is in your mp4 :). Can you show the full terminal output from just:

```
ffmpeg -i in.mp4
```

Any special reason for the avi container?

no reason really but I would like to convert the mp4 to avi with same bit rate and all the rest the same

ffmpeg -i in.mp4
 ```

FFmpeg version 0.6.5, Copyright (c) 2000-2010 the FFmpeg developers                                  
  built on Jan 29 2012 17:52:15 with gcc 4.4.5 20110214 (Red Hat 4.4.5-6)                            
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --disable-avisynth --extra-cflags='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector --param=ssp-buffer-size=4 -m64 -mtune=generic -fPIC' --enable-avfilter --enable-avfilter-lavf --enable-libdc1394 --enable-libdirac --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libx264 --enable-gpl --enable-nonfree --enable-postproc --enable-pthreads --enable-shared --enable-swscale --enable-vdpau --enable-version3 --enable-x11grab                                                                                                                         
  libavutil     50.15. 1 / 50.15. 1                                                                                         
  libavcodec    52.72. 2 / 52.72. 2                                                                                         
  libavformat   52.64. 2 / 52.64. 2                                                                                         
  libavdevice   52. 2. 0 / 52. 2. 0                                                                                         
  libavfilter    1.19. 0 /  1.19. 0                                                                                         
  libswscale     0.11. 0 /  0.11. 0                                                                                         
  libpostproc   51. 2. 0 / 51. 2. 0                                                                                         
[aac @ 0x26a62d0]Transition from an ONLY_LONG or LONG_STOP to an EIGHT_SHORT sequence detected. If you heard an audible artifact, please submit the sample to the FFmpeg developers.                                                                    
    Last message repeated 1 times
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x269d670]max_analyze_duration reached

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'in.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 1
    compatible_brands: mp42isom
  Duration: 00:03:56.80, start: 0.000000, bitrate: 3931 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 3798 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 30k tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 127 kb/s
    Stream #0.2(eng): Data: mp4s / 0x7334706D, 4320 kb/s
    Stream #0.3(eng): Data: mp4s / 0x7334706D, 3840 kb/s

```

---

### Post by andrew.46 on 2012-12-19
I am not sure that aac sound lives well in avi container but perhaps you could simply try:
```

ffmpeg -i in.mp4 -acodec copy -vcodec copy out.avi
```

I am guessing the syntax a little here as your copy of FFmpeg is a little old :). If playback barfs on this one try converting the sound to mp3 and this *will *work with avi...
```

-acodec libmp3lame 
```

---

### Post by sohlinux on 2012-12-19
> **andrew.46 said:**
> I am not sure that aac sound lives well in avi container but perhaps you could simply try:
```

ffmpeg -i in.mp4 -acodec copy -vcodec copy out.avi
```

I am guessing the syntax a little here as your copy of FFmpeg is a little old :). If playback barfs on this one try converting the sound to mp3 and this *will *work with avi...
```

-acodec libmp3lame 
```

thanks that worked :)

---

### Post by andrew.46 on 2012-12-19
Great news :). Mind you if you want to get serious about FFmpeg it would not hurt to visit this great guide sometime:

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

This will unlock a great deal more of the FFmpeg magic...

---

### Post by sohlinux on 2012-12-19
> **andrew.46 said:**
> Great news :). Mind you if you want to get serious about FFmpeg it would not hurt to visit this great guide sometime:

Compile FFmpeg on Ubuntu
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

This will unlock a great deal more of the FFmpeg magic...

great link ;)

---

### Post by dannyboy79 on 2012-12-19
i wasn under the impression you could merely rename a .mp4 to .avi, is that not true? after all, it's merely a container and nothing more.

---

### Post by andrew.46 on 2012-12-19
> **dannyboy79 said:**
> i wasn under the impression you could merely rename a .mp4 to .avi, is that not true? after all, it's merely a container and nothing more.

I would be surprised, I believe remuxing is necessary. But I have been wrong many times before :)

---

### Post by evilsoup on 2012-12-19
There are differences between container formats, more than just the name: where and how metadata is stored in the file is the most significant one.

I know from experience that some FLV files are close enough to MP4 that renaming them was enough to get my PS3 to play them; but many are not. The same may be true with AVI files, I suppose it would depend on how exactly they were encoded and what decoder (player) you're using. It will always be safer to just remux the files into a new container, and even on my atom-based netbook that doesn't take very long.

---

### Post by AstroLlama on 2012-12-20
be sure to read up on ffmpeg! It took me lots of experimenting and man page reading to figure out how to retain stereo separation, bitrate, etc. I eventually figured it all out for my objectives, but always look deeper into terminal "one liners" because sometimes the results don't match what you expect! and of course if it's sucessful report back and share the knowledge :)

[http://rodrigopolo.com/ffmpeg/cheats.html](http://rodrigopolo.com/ffmpeg/cheats.html)
here's a great little cheat sheet as reference

---

