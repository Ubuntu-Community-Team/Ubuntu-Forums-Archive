---
title: "[SOLVED] Transcoding h264 mp4 via mediatomb for ps3."
date: 2008-08-18
forum: Multimedia Software
---

### Post by FooAtari on 2008-08-18
Ok, I have been using Mediatomb to play my video files on the ps3, most of my files seem to work fine, excpet for the mp4's I have, they show as unsupported format.

I have been trying to fix this for days, but most information I have found does not relate to my issue and the few guides I have found don't seem to work.  Hopefully someone here can help.

I did ffmpeg -i on one of the files, and got the following information;

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '300.mp4':
  Duration: 01:44:34.0, start: 0.000000, bitrate: 2668 kb/s
  Stream #0.0(eng): Video: h264, yuv420p, 720x428, 25.00 fps(r)
  Stream #0.1(eng): Audio: mp4a / 0x6134706D, 48000 Hz, stereo
  Stream #0.2(eng): Data: text / 0x74786574
Must supply at least one output file
```

So thats the type of file I want to setup transcoding for.

Here is the profile for doing this I have created in the mediatomb config.xml I found this information in another guide.
```

<profile name="ffmpeg-sh" enabled="yes" type="external">
	<mimetype>video/mpeg</mimetype>
	<accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <agent command="/usr/bin/ffmpeg-tr" arguments="%in %out"/>
	<buffer size="6144000" chunk-size="131072" fill-size="2048000"/>
</profile>
```

Here is the ffmpeg-tr script;

```
exec /usr/bin/ffmpeg -i "$1" -f mpegts -sameq -ac 2 -ar 44100 -threads 2 - > "$2"
```


However this script/transcoding profile doesn't work, probably because it doesn't relate to the codec of the video files?

Any help/pointers on how to get these mp4's playing would be very much appreciated.

---

### Post by FooAtari on 2008-08-19
anyone? 

looks like might have to do this the hard way. Ill post if I fix it :)

---

### Post by FooAtari on 2008-08-19
The problem was with the audio.  I had to compile ffmpeg with libfaad to allow mp4a support.

---

### Post by sportsdude81 on 2009-09-29
What did you do? Having the same problem I really don't understand your solution.

---

### Post by FooAtari on 2009-09-30
Take a look here

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

