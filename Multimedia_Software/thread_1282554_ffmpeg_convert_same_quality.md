---
title: "ffmpeg convert same quality"
date: 2009-10-04
forum: Multimedia Software
---

### Post by rashwan on 2009-10-04
Hello ,

how to convert .avi file to .mpg with the exact quality of the original file ?

tried: > ffmpeg -i input.avi output.mpg

but it wasnt the same quality

---

### Post by dhughes on 2009-10-04
This is a nice how-to: [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

 But yeah the container/codec relationship can be confusing, in your case I guess you want to change the container type but keep the same codec whatever that is, on the file if you right-click>properties>Audio/Video what does it show for a codec?

 I'm not much help but at least a bump.

---

### Post by SuperSonic4 on 2009-10-04
Some will be lost but if you know what you're doing it can be negligible

```
ffmpeg -i input.avi -sameq -vcodec -libx264 -acodec libfaac ouput.mp4
```

---

### Post by rashwan on 2009-10-04
> **dhughes said:**
> This is a nice how-to: [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

 But yeah the container/codec relationship can be confusing, in your case I guess you want to change the container type but keep the same codec whatever that is, on the file if you right-click>properties>Audio/Video what does it show for a codec?

 I'm not much help but at least a bump.

Dimensions: 608 x 336

Codec: XVID MPEG-4

Framrate: 25 frames per second

Bitrate: N/A

any tips ?

> **SuperSonic4 said:**
> Some will be lost but if you know what you're doing it can be negligible

```
ffmpeg -i input.avi -sameq -vcodec -libx264 -acodec libfaac ouput.mp4
```


does this will convert it to mp4 or mpg , or no different ?

sorry for asking a lot , am totally newbie

thanks

---

### Post by SuperSonic4 on 2009-10-04
> **rashwan said:**
> Dimensions: 608 x 336

Codec: XVID MPEG-4

Framrate: 25 frames per second

Bitrate: N/A

any tips ?



does this will convert it to mp4 or mpg , or no different ?

sorry for asking a lot , am totally newbie

thanks

Don't worry, it's good you pointed it out. That will convert to mp4 because I misread the original post.

```
ffmpeg -i input.avi -sameq -vcodec libx264 -acodec libmp3lame output.mpg
```

---

### Post by rashwan on 2009-10-04
Here is what i got: 
```
ffmpeg -i *.avi -sameq -vcodec libx264 -acodec libmp3lame output.mpg
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:20, gcc: 4.4.1
Input #0, avi, from 'Earth 2009 DVDRip XviD.avi':
  Duration: 01:35:00.04, start: 0.000000, bitrate: 1027 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 608x336 [PAR 1:1 DAR 38:21], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 80 kb/s
_Unknown encoder 'libx264'_
```

well i guess that is the main reason: Unknown encoder 'libx264'

IC , i have to manually install x264

i'll install it and give a try

---

### Post by dhughes on 2009-10-04
You can use VLC media player, start VLC then do this:

 Media>Open File (choose the media file you want to convert)>Convert (bottom right corner drop down box arrow, next to the "Play" button)>Profile (choose Windows wmv/asf)>Save

 It will, I assume, convert it to the correct container and codec or you can actually choose which container, video codec and audio codec you want by manually selecting each from the Profile tabs.

 I'm converting a Diggnation h.264 mp4 to a wmv (asf codec?)right now I'll let you know how it works out.

edit: As Supersonic mentioned I'm pretty sure you'll lose some quality since you're converted something again and it will probably degrade the quality.

---

### Post by andrew.46 on 2009-10-04
Hi rashwan,

> **rashwan said:**
> how to convert .avi file to .mpg with the exact quality of the original file ?

Is there a particular reason that you are after mpg? This imposes some pretty substantial limitations on your encoding options that would not be seen in containers like mp4 or matroska. The *default* codecs for such an encode under FFmpeg, which is what you have seen, are mpeg1video audio and mp2 audio.

Andrew

---

### Post by FakeOutdoorsman on 2009-10-04
> **SuperSonic4 said:**
> Don't worry, it's good you pointed it out. That will convert to mp4 because I misread the original post.

```
ffmpeg -i input.avi -sameq -vcodec libx264 -acodec libmp3lame output.mpg
```

The *-sameq* option is not compatible with libx264.  Also, I believe the mpg container format does not officially support H.264 video.  If you want to encode H.264 video using libx264 you should be using the libx264 presets:

```
ffmpeg -i input.avi -acodec libfaac -ab 128k -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
```

You can see more examples at [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/). Ubuntu Jaunty Jackalope 9.04 can use the presets, but restricted encoders need to be enabled:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Ubuntu Karmic Koala 9.10 removed libfaac support from FFmpeg due to ambiguous license issues, so you will need to compile FFmpeg to take advantage of encoding to AAC audio:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---

### Post by FakeOutdoorsman on 2009-10-04
> **rashwan said:**
> 
well i guess that is the main reason: Unknown encoder 'libx264'

IC , i have to manually install x264

I'm guessing you're using Ubuntu Karmic Koala 9.10.  You do not need to manually install x264, but instead you can install **libavcodec-extra-52**.  This package will enable restricted encoders in FFmpeg including libx264, but not libfaac as you can see in my threads above.  Right now I recommend Karmic users to compile their own FFmpeg to gain access to AAC encoding.

---

### Post by dhughes on 2009-10-04
The good news, VLC worked and was easy to figure out just point and click what you want, although the options are almost hidden.

 The bad news is it took almost an hour to convert the 500MB h.264 mp4 to a 370MB wmv Windows media 8 codec and it looks absolutely horrible.

 I think that's the big problem when converting not just X to Y but what will it look like after converting? You want high quality but you don't want to wait forever and you have to know what will work on whatever you'll be playing it on.

---

### Post by andrew.46 on 2009-10-04
Hi dhughes,

> **dhughes said:**
> I think that's the big problem when converting not just X to Y but what will it look like after converting? You want high quality but you don't want to wait forever and you have to know what will work on whatever you'll be playing it on.

My own method is to transcode a small section of a file to start with, making multiple changes until I know that it will look ok. Then run the main transcode overnight. Easy enough to do with FFmpeg, I am not so sure about vlc though...

Andrew

---

