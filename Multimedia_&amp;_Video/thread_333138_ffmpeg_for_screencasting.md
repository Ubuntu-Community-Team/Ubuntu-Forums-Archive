---
title: "ffmpeg for screencasting"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by Seine on 2007-01-07
I'm am trying to capture screencast using ffmpeg without luck.

FFMPEG Version:
```
jem@fawkes:~$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
ffmpeg      SVN-rUNKNOWN
libavutil   3211264
libavcodec  3345152
libavformat 3278080

```

Using [the example in the ffmpeg doco](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC4) I get the following error.

```
jem@fawkes:~$ ffmpeg -f x11grab -vd x11:0.0 /tmp/out.mpgFFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Unknown input or output format: x11grab

```

Using the example from [this blog](http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/) I get a different error.

```
jem@fawkes:~$ ffmpeg -vcodec mpeg4 -b 1000 -r 10 -g 300 -vd x11:0,0 -s 1024x768 ~/test.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Cannot open video device x11:0,0 : No such file or directory
Could not find video grab device

```

Being a beginner at this I have no idea what to do next. Google and Ubuntuforum searches didn't help.

Can anyone point me in the right direction?

Thanks
Seine

---

### Post by Seine on 2007-01-07
PS DISPLAY=:0.0, so I assume x11:0.0 is the correct value for the -vd flag.

---

### Post by Seine on 2007-01-07
I haven't been able to progress any further with this issue. Apologies for this one and only bump.

---

### Post by richardq on 2007-02-03
You're using the same command as I am to record a screencast. I can record successfully using the -s 800x600 resolution but it doesn't work for 1024x768 or 1280x1024 resolution on my machine. It either crashes ffmpeg or produces an avi file that won't play on any of my media players whenever I go higher than 800x600 :(  I couldn't reproduce your error, but I do remember seeing that one on my machine as well. Try reducing the resolution and see if it works. 

BTW - I'm assuming you used the patched ffmpeg to do the recording. I followed these instructions ([http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/](http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/)) but I know there are other methods out there.

Good luck.

---

### Post by alina.bolero on 2007-11-30
I need to create a live streaming MPEG-4 screencast from inside Gutsy.  The ffmpeg file and patch from the blog noted just return a server error for me.

Is there somewhere else I can get it from?

-Alina

---

