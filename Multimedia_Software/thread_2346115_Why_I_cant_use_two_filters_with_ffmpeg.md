---
title: "Why I cant use two filters with ffmpeg"
date: 2016-12-11
forum: Multimedia Software
---

### Post by vidovic-slobodan on 2016-12-11
Hey guys how I can set font and font size with ffmpeg here is mine ffmpeg command

```
ffmpeg 
ffmpeg version 2.8.8-0ubuntu0.16.04.1 Copyright (c) 2000-2016 the FFmpeg developers
  built with gcc 5.4.0 (Ubuntu 5.4.0-6ubuntu1~16.04.2) 20160609
  configuration: --prefix=/usr --extra-version=0ubuntu0.16.04.1 --build-suffix=-ffmpeg --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --cc=cc --cxx=g++ --enable-gpl --enable-shared --disable-stripping --disable-decoder=libopenjpeg --disable-decoder=libschroedinger --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmodplug --enable-libmp3lame --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librtmp --enable-libschroedinger --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzvbi --enable-openal --enable-opengl --enable-x11grab --enable-libdc1394 --enable-libiec61883 --enable-libzmq --enable-frei0r --enable-libx264 --enable-libopencv
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libavresample   2.  1.  0 /  2.  1.  0
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'
```
And here is mine usage of it

```
ffmpeg -i movie.avi -strict -2 -vf subtitles=subtitle.srt:force_style='FontName=ubuntu,Fontsize=30' -qscale:v 3 outtst.avi
```
Im getting error 

```
AVFilterGraph @ 0x2229f20] No such filter: 'Fontsize'
```

---

### Post by mc4man on 2016-12-11
Really don't know jack about this but maybe try quoting the complete vf used, like (quotes shown in red - 
```
[COLOR="#FF0000"]"[/COLOR]subtitles=subtitle.srt:force_style='FontName=ubuntu,Fontsize=30'[COLOR="#FF0000"]"[/COLOR]
```

---

### Post by vidovic-slobodan on 2016-12-11
> **mc4man said:**
> Really don't know jack about this but maybe try quoting the complete vf used, like (quotes shown in red - 
```
[COLOR=#FF0000]"[/COLOR]subtitles=subtitle.srt:force_style='FontName=ubuntu,Fontsize=30'[COLOR=#FF0000]"[/COLOR]
```

Thts it many many tnx

---

