---
title: "convert mp4 to mp3 script"
date: 2009-05-22
forum: Multimedia Software
---

### Post by rustysail on 2009-05-22
Hello

I have a bunch of mp4s that I want to put on my ipod.  I have converted them individually before but it takes forever, so I wrote this script, but it doesn't work.

#!/bin/bash
FILES="*.mp4"
echo $FILES
a=1
for f in "$FILES"
do
	echo "Processing $f file..."
	ffmpeg -i $f -vn -ac $a.mp3
	a=$a+1
done


however, it comes up with an error.  I'm not great at bash so I'm not sure whats going on.

Processing *.mp4 file...
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 1 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Aaron_Tippin_-_You_ve_Got_To_Stand_For_Something.mp4':
  Duration: 00:03:00.48, start: 0.000000, bitrate: 309 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 320x240, 25 tbr, 25 tbn, 50 tbc
File 'Alan_Jackson_-_Country_Boy.mp4' already exists. Overwrite ? [y/N] n
Not overwriting - exiting

thanks a lot.
Rusty

---

### Post by andrew.46 on 2009-05-22
Hi rustysail,

Your copy of FFmpeg needs to be capable of outputting mp3:

```

andrew@skamandros~$ **[COLOR="Purple"]ffmpeg -formats | grep libmp3lame[/COLOR]**
FFmpeg version SVN-r18813, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab
 **[COLOR="Purple"]--enable-libmp3lame[/COLOR]** --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb 
--enable-libgsm --enable-libspeex --enable-zlib --enable-nonfree 
--enable-gpl
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.29. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 13 2009 19:10:11, gcc: 4.2.4
  **[COLOR="Purple"]EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)[/COLOR]**

```

I suspect your copy does *not* have this capability and if this is true have a look at:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

If this is all in place you could try a 'for' loop similar to yours, the most notable difference being the naming convention and the inclusion of an audio bitrate:

```

for f in *.mp4; do ffmpeg -i $f -acodec libmp3lame -ab 128k $(echo $f | sed 's/\.mp4$/\.mp3/'); done

```

This might be just as easy as a copy and paste job rather than a formal script?

All the best,

Andrew

---

### Post by KyleBrandt on 2009-05-22
When you put an asterisk in double quotes it is literal, not a glob.

I don't know this particular case, but basically you want:

```

for i in *.mp3; do
   magic_convert --input="$i" --output=="${i%*.mp4}.mp3"
done

```

The double quotes are important so file names with spaces still work

---

### Post by rustysail on 2009-05-22
Thanks a lot guys that worked perfectly.

---

