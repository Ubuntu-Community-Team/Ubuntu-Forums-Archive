---
title: "How do I convert OGG to AVI?"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Stabilityonitsown on 2008-05-01
I have searched through so many sites and tried so many varietys to convert but none has worked so far. Can you guys help me?

---

### Post by Elderon on 2008-05-01
You're trying to convert a sound format to a video format?  Are you adding a soundtrack to a video?

I haven't kept up with OGG development that much, so perhaps I'm wrong.

---

### Post by Stabilityonitsown on 2008-05-01
Ogg is video.

---

### Post by Th3Professor on 2008-05-01
> **Stabilityonitsown said:**
> Ogg is video.

Ogg's a container - multiple "ogg" formats are out there, in both video and audio, lossless and lossy. A popular audio version is "vorbis" and video version is "theora".

---

### Post by cor2y on 2008-05-01
mencoder can it the same way it can convert mkv to avi.
```
 mencoder input.ogm -oac mp3lame -lameopts cbr:br=128 -ovc copy -o output.avi
```Maybe you need it to be xvid or mpeg4 compliant then convert using xvid or mpeg4 via lavc
```
 mencoder inpt.ogm -oac mp3lame -lameopts cbr:br=128 -ovc xvid -xvidencopts pass=1 -o output.avi
``````
 mencoder inpt.ogm -oac mp3lame -lameopts cbr:br=128 -ovc lavc -ffourcc DX50 -lavcopts vcodec=mpeg4 -o output.avi
```There are many settings you can play with such as lame bitrate etc, using the xvid quantizier instead of the pass argument or specificly set the video bitrate for both xvid or lavc mpeg4 as well as more than one pass although thats overkill and wasteful (time it takes to encode) in most cases.

---

### Post by Th3Professor on 2008-05-01
> **Stabilityonitsown said:**
> I have searched through so many sites and tried so many varietys to convert but none has worked so far. Can you guys help me?

Have you tried:
```
mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc
```

...that's from:
[http://ubuntuswitch.wordpress.com/2007/10/05/howto-convert-ogg-to-avi-with-mencoder/](http://ubuntuswitch.wordpress.com/2007/10/05/howto-convert-ogg-to-avi-with-mencoder/)

[LIST]
[*]**out.ogg** is the .ogg-file you want to convert
[*]**out.avi** is the .avi-file you want to create
[*]**mp3lame** is the used audio-codec  (here mp3)
[*]**lavc** is the used video-codec (here libavcodec)
[/LIST]
This site talks about converting avi to ogg, you can take the concept and try to reverse it for ogg to avi:
[http://www.dogphilosophy.net/SECTION-Technical_Stuff/ogg-theora-microhowto.html](http://www.dogphilosophy.net/SECTION-Technical_Stuff/ogg-theora-microhowto.html)

You might also try:
```
ffmpeg -i inputmovie.ogg -target ntsc-dv output.dv
```

...that's from:
[http://ubuntuforums.org/archive/index.php/t-481778.html](http://ubuntuforums.org/archive/index.php/t-481778.html)

Here's another mencoder approach from the link above:
```
mencoder -idx your_input.ogg -vf scale=640:480 -ovc lavc -oac mp3lame -o your_output.avi
```

Another bit from the same link mentions 3 choices:
"1. gmencoder (or mencoder)
2. winff (or ffmpeg)
3. avidemux"

Enabling theora support in mencoder:
"make sure u r correctly install all theora tools (ie libtheora0)........"
And mention of mplayer preferences:
"or change ur audio and video codecs with right click-> preferences of mplayer"

Another individual in the same link had one simple command:
```
ffmpeg -i file.ogg  file.avi
```

You might also look into ffmpeg2theora.

This talks about making oggs, though might come in handy anyway:
[http://free-electrons.com/community/videos/mini-howto](http://free-electrons.com/community/videos/mini-howto)

---

### Post by Stabilityonitsown on 2008-05-02
Well here is what I came up with:(.
```
shooter:/home/shooter#
shooter:/home/shooter#
shooter:/home/shooter# mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc
MEncoder 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

File not found: 'out.ogg'
Failed to open out.ogg.
Cannot open file/device.

Exiting...
shooter:/home/shooter# sudo mencoder out.ogg -o out.avi -oac mp3lame -ovc lavc
MEncoder 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

File not found: 'out.ogg'
Failed to open out.ogg.
Cannot open file/device.

Exiting...
shooter:/home/shooter# ffmpeg -i out.ogg -target ntsc-dv output.dv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 26 2007 15:50:40, gcc: 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)
out.ogg: I/O error occured
Usually that means that input file is truncated and/or corrupted.
shooter:/home/shooter# ffmpeg -i out.ogg  file.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 26 2007 15:50:40, gcc: 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)
out.ogg: I/O error occured
Usually that means that input file is truncated and/or corrupted.
shooter:/home/shooter# mencoder out.ogm -oac mp3lame -lameopts cbr:br=128 -ovc copy -o output.avi
MEncoder 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

File not found: 'out.ogm'
Failed to open out.ogm.
Cannot open file/device.

Exiting...
shooter:/home/shooter# mencoder out.ogg -oac mp3lame -lameopts cbr:br=128 -ovc copy -o output.avi
MEncoder 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.53GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

File not found: 'out.ogg'
Failed to open out.ogg.
Cannot open file/device.

Exiting...
shooter:/home/shooter#


```

---

### Post by eye208 on 2008-05-02
> **Stabilityonitsown said:**
> File not found: 'out.ogg'
Failed to open out.ogg.
Uh-oh ... your video has the wrong file name. Tough luck! You have to delete it, then make a new video, but this time save it as "out.ogg". This is the only way to make the command lines work!

:lolflag:

---

### Post by howlingmadhowie on 2008-05-02
> **eye208 said:**
> Uh-oh ... your video has the wrong file name. Tough luck! You have to delete it, then make a new video, but this time save it as "out.ogg". This is the only way to make the command lines work!

:lolflag:

just for the sake of clarity, eye208 is being sarcastic here. you can also change 'out.ogg' or 'out.ogm' into the name of your file. you can find the name of your file by using the cd command to navigate to the directory your file is in and then the ls command to list all the files in the directory.

---

### Post by Stabilityonitsown on 2008-05-02
OMG THANK YOU THANK YOU SOOOO MUCH GUYS IT WORKED IT FINALLY WORKED OMG WTF THIS IS SO AWESOME! It worked using 
```
ffmpeg -i out.ogg file.avi
``` and it wouldn't have worked if it wasn't for the one who suggested making it "out.ogg". Thanks every!!!!!!!!!!!!!!!! PLENTY OF KISSES GOES OUT TO EVERYONE IN THIS THREAD WHO HELPED!!!!!!!!!!!!!!!!!!!!!111111ONEONEONE

---

### Post by Th3Professor on 2008-05-02
> **Stabilityonitsown said:**
> OMG THANK YOU THANK YOU SOOOO MUCH GUYS IT WORKED IT FINALLY WORKED OMG WTF THIS IS SO AWESOME! It worked using 
```
ffmpeg -i out.ogg file.avi
``` and it wouldn't have worked if it wasn't for the one who suggested making it "out.ogg". Thanks every!!!!!!!!!!!!!!!! PLENTY OF KISSES GOES OUT TO EVERYONE IN THIS THREAD WHO HELPED!!!!!!!!!!!!!!!!!!!!!111111ONEONEONE

Cool beans. Glad to have been helpful.

---

### Post by Elderon on 2008-05-04
> **Stabilityonitsown said:**
> Ogg is video.

OGG is no longer "video".

OGG is the container file that could contain video, but back in like 2006 the foundation that runs OGG stated that OGG was to be used for audio only.

---

### Post by Th3Professor on 2008-05-04
> **Elderon said:**
> OGG is no longer "video".

OGG is the container file that could contain video, but back in like 2006 the foundation that runs OGG stated that OGG was to be used for audio only.

Ogg still is video, actually, though it's audio too. It's video, audio, and subtitles/etc.-type formats. The actual "file extension" varies, depending on which version is used, yet it is all still part of the container - could be vorbis, theora, etc.

---

