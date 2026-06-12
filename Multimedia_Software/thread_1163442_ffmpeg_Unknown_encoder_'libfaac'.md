---
title: "ffmpeg: Unknown encoder 'libfaac'"
date: 2009-05-18
forum: Multimedia Software
---

### Post by Matl on 2009-05-18
Hello,

I compiled ffmpeg WITH (!) libfaac support. Now when I run 

```
ffmpeg -i audio.dts -acodec libfaac -aq 255 -ar 44100 -ac 2 -async 1 -vsync 1 audio.aac
```

I get the following output

```

FFmpeg version SVN-r18868, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr/local --enable-gpl --enable-nonfree --enable-shared --enable-postproc --enable-avfilter --enable-avfilter-lavf --enable-pthreads --enable-x11grab --enable-bzlib --enable-libamr-nb --enable-libamr-wb --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libnut --enable-libschroedinger --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.29. 0 / 52.20. 0
  libavformat   52.32. 0 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libavfilter    0. 5. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on May 18 2009 23:48:22, gcc: 4.3.3
[dca @ 0x8f50d30]Stream with high frequencies VQ coding
Input #0, dts, from 'audio.dts':
  Duration: 01:58:14.03, bitrate: 1535 kb/s
    Stream #0.0, 1/90000: Audio: dca, 48000 Hz, 5.1, s16, 1536 kb/s
Unknown encoder 'libfaac'

```

As you can see, --enable-libfaac is in the config options. What did I do wrong?

Thanks,

Matl

---

### Post by FakeOutdoorsman on 2009-05-18
Since you included *--enable-shared* you will need to run **sudo ldconfig** after FFmpeg installation to update the shared library links.  Also, I am unfamiliar with *--enable-libfaadbin*, but it may be causing issues.  If none of these suggestions help you can follow my guide (your command works with my SVN FFmpeg):
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---

### Post by Matl on 2009-05-19
Hello,

I did indeed a ldconfig. But not I tried it without --enable-shared and --enable-libfaadbin

With ffmpeg -formats I now have libfaac as encoder (that wasn't before).


And now it works. Seems like there is really a issue. I pasted the installation from another guide because I had to make it quick

Thanks for your help.

Martin

---

### Post by juros on 2011-02-08
Ubuntu 10.04 (64 bit) and 10.10 (64 bit) have the same error with installed Medibuntu packages. The following command will fix this:
```

sudo cp /usr/lib/libfaad.so.2 /usr/lib/libfaad.so.0

```

Ubuntu has several of these missing link bugs (e.g. /usr/lib32/libstdc++.so -> libstdc++.so.6 because of obsolete libstdc++.so.5). ldconfig will not always help.

---

### Post by Torxed on 2011-04-28
For all those using Ubuntu 10.10:

Either with trying to convert manually via ffmpeg and the codec libfaac OR with the Ruby script "mp4ize".


First of all, libfaac dosn't work in 10.10, at least not with ffmpeg.
Use "acc" instead.



mp4ize users:
* nano mp4ize
* find the row containing DEFAULT_ARGS and libfaac
* replace "libfaac" with "aac" (without the bunny-ears)
  (and you need to add "-strict experimental" at the end too)

Your DEFAULT_ARGS should look something like:
DEFAULT_ARGS = "-f mp4 -y -vcodec libxvid -maxrate 1000 -mbd 2 -qmin 3 -qmax 5 -g 300 -acodec aac -strict experimental"



same goes for ffmpeg users,
swithc audio-codec to "acc" and add "-strict experimental" and you should be rockin your boat in no time *brings in the flippy-floppys*

---

### Post by anchepiece on 2011-05-03
Torxed, 
As of May 2 the mp4ize project has been updated to reflect the codec changes.

see: [http://thomer.com/howtos/ipod_video.html](http://thomer.com/howtos/ipod_video.html)
ruby version: [http://thomer.com/howtos/mp4ize](http://thomer.com/howtos/mp4ize)
python version: [http://github.com/anchepiece/mp4ize-python](http://github.com/anchepiece/mp4ize-python)

Thanks!

---

### Post by doug-M on 2011-05-12
For ffmpg users on 10.0 look here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Specifically these commands:

Download medibuntu repository list:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

Grab the extras with restricted codecs:
```
sudo apt-get install ffmpeg libavcodec-extra-52
```

---

### Post by Larian on 2011-11-09
@ Doug-M

Your solution to install the missing libraries did the trick.

---

