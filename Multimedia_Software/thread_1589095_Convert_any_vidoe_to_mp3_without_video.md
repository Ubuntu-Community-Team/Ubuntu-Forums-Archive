---
title: "Convert any vidoe to mp3 without video"
date: 2010-10-05
forum: Multimedia Software
---

### Post by nomanslan369 on 2010-10-05
I been looking on Google to convert videos to mp3 audio and all I get is just a video conversion from one format to another and some things I installed just get error messages so I took them back off. Anyone know the proper syntax in Mencorder to convert a video just to audio? Or any other program I can use that won't cause this much trouble? I been trying for well over an hour now...

---

### Post by aadam12 on 2010-10-05
Try this gui - Hyper Video Converter. It will create the commands for mencoder or ffmpeg and then do the conversion as well.
_[http://hypervideoconve.sourceforge.net/](http://hypervideoconve.sourceforge.net/)_[]("http://sourceforge.net/projects/hypervideoconve/")

---

### Post by amauk on 2010-10-05
FFmpeg can work out what you want to do (strip out audio only, for example) based on file extensions

Eg.```
ffmpeg -i video.avi audio.mp3
```

---

### Post by nomanslan369 on 2010-10-05
Many thanks to both of you hahaha, I swear; this place is a life saver lolz.

So wait, how do I convert flv files to audio... its doing anything for me at all with the ffmpeg.

I installed "lame", readings some where on the internet that I need to convert fvl to mp3 with ffmpeg... here is what happens...


nomanslan@nomanslan-box:~/Desktop$ ffmpeg -i test.flv -ar 44100 -ab 160k -ac 2 t.mp3
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, flv, from 'test.flv':
  Duration: 00:06:40.96, start: 0.000000, bitrate: 158 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 94 kb/s, 30 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 64 kb/s
File 't.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to 't.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 160 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
nomanslan@nomanslan-hackbox:~/Desktop$

[B]And then I open the file and there is still an error that says "An error occurred:  Stream contains no data"

Another Edit:[/B]
I just changed the .flv extension to .mp3 on the file itself than ran -i cmd and all worked perfected. Thank you!

---

### Post by andrew.46 on 2010-10-06
Hi nomanslan,

Note that your original input .flv file actually contains mp3 audio already:

```

Stream #0.0: Video: flv, yuv420p, 320x240, 94 kb/s, 30 tbr, 1k tbn, 1k tbc
**[COLOR="Red"]Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 64 kb/s[/COLOR]**

```

thus re-encoding is not necessary, all you need is:

```
ffmpeg -i test.flv -acodec copy test.mp3
```

and the mp3 sound will be *copied* over to a new file.

Andrew

---

### Post by amauk on 2010-10-06
As noted above, the flv contains an mp3 stream, so you can use the copy function to copy streams without reencoding

but just for reference,> **nomanslan369 said:**
> Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
Looks like you don't have the FFmpeg mp3 encoder (it's not installed by default due to patent laws in USA)

install libavcodec-extra package for full encoder support (including encoding mp3)

---

### Post by SeijiSensei on 2010-10-06
For mencoder, you can use '-vo null' to send the video stream to the trash.

---

### Post by nomanslan369 on 2010-10-07
Thank you for all the help... Linux just keeps getting better and better lolz.

---

