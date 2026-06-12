---
title: "Update killed FFMPEG? I think..."
date: 2009-03-18
forum: Multimedia Software
---

### Post by jmap82 on 2009-03-18
[B]I'm hesitant to say that this problem is solved, but it isn't the problem I thought it was.  You're welcome to read this thread, but a more thorough synopsis of what happened has been documented here: [http://jmap82.com/term-output]("http://jmap82.com/term-output")
Sorry for the inconvenience.[/B]

Last night I recorded my desktop using recordmydesktop, which only produces .ogv files (as far as I know).  I downloaded ffmpeg to convert the files to mp4.  It worked great.

This morning I wake up and ubuntu wants to update.  So I let it, but know ffmpeg doesn't work.  It "processes" the video, but no matter what I convert to all I get are grey frames.

This is what was updated.

```
Commit Log for Wed Mar 18 09:05:20 2009


Upgraded the following packages:
ffmpeg (3:0.svn20080206-12ubuntu3) to 3:0.svn20080206-12ubuntu3.1
gstreamer0.10-alsa (0.10.21-3) to 0.10.21-3ubuntu0.1
gstreamer0.10-gnomevfs (0.10.21-3) to 0.10.21-3ubuntu0.1
gstreamer0.10-plugins-base (0.10.21-3) to 0.10.21-3ubuntu0.1
gstreamer0.10-plugins-base-apps (0.10.21-3) to 0.10.21-3ubuntu0.1
gstreamer0.10-plugins-good (0.10.10.4-1ubuntu1) to 0.10.10.4-1ubuntu1.1
gstreamer0.10-pulseaudio (0.10.10.4-1ubuntu1) to 0.10.10.4-1ubuntu1.1
gstreamer0.10-x (0.10.21-3) to 0.10.21-3ubuntu0.1
libavdevice52 (3:0.svn20080206-12ubuntu3) to 3:0.svn20080206-12ubuntu3.1
libavformat52 (3:0.svn20080206-12ubuntu3) to 3:0.svn20080206-12ubuntu3.1
libavutil49 (3:0.svn20080206-12ubuntu3) to 3:0.svn20080206-12ubuntu3.1
libglib2.0-0 (2.18.2-0ubuntu2) to 2.18.2-0ubuntu2.1
libglib2.0-data (2.18.2-0ubuntu2) to 2.18.2-0ubuntu2.1
libgstreamer-plugins-base0.10-0 (0.10.21-3) to 0.10.21-3ubuntu0.1
libpostproc51 (3:0.svn20080206-12ubuntu3) to 3:0.svn20080206-12ubuntu3.1
libswscale0 (3:0.svn20080206-12ubuntu3) to 3:0.svn20080206-12ubuntu3.1

```

I rolled back the ffmpeg install and that didn't fix it, so I figure it might be on of the lib packages, but I can't roll those back. or uninstall them because of their dependences... so it seems...

Any help is much appreciated.

---

### Post by jmap82 on 2009-03-18
Bump...

---

### Post by Rocket2DMn on 2009-03-18
Moved to Multimedia & Video - hopefully you can get more help here.  Good luck.

---

### Post by jmap82 on 2009-03-18
> **Rocket2DMn said:**
> Moved to Multimedia & Video - hopefully you can get more help here.  Good luck.
Thanks, Rocket2DMn, I was just researching how to request it to be moved. :)

---

### Post by andrew.46 on 2009-03-18
Can you post the full command that you use + the complete terminal output that follows? This should give a hint as to what is going on.

All the best,

Andrew

---

### Post by jmap82 on 2009-03-19
Thanks for your interest.

Unfortunately, I've been try a bunch of different things to try to fix the problem myself, and I seem to have broken it worse... but here is the output nonetheless. 

I try to stick with the defaults, its less confusing that way...

```
jmap82@JMAP2:~$ ffmpeg -i Desktop/OneCube-DarkKnightSetup.ogv Desktop/OneCube-DarkKnightSetup.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[theora @ 0xb7d552f0]Theora bitstream version 30201
[theora @ 0xb7d552f0]560 bits left in packet 81
[theora @ 0xb7d552f0]7 bits left in packet 82
Input #0, ogg, from 'Desktop/OneCube-DarkKnightSetup.ogv':
  Duration: 00:00:53.2, start: 0.333333, bitrate: 1879 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 3200x1200 [PAR 1:1 DAR 8:3], 24.00 tb(r)
Output #0, mp4, to 'Desktop/OneCube-DarkKnightSetup.mp4':
    Stream #0.0: Video: 0x0000, yuv420p, 3200x1200 [PAR 1:1 DAR 8:3], q=2-31, 200 kb/s, 24.00 tb(c)
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
jmap82@JMAP2:~$ 

```
This is a new occurance for mp4 and avi destination files.  Typical output for other formats look like this:
```
jmap82@JMAP2:~$ ffmpeg -i Desktop/OneCube-DarkKnightSetup.ogv Desktop/OneCube-DarkKnightSetup.mpg
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[theora @ 0xb7f1a2f0]Theora bitstream version 30201
[theora @ 0xb7f1a2f0]560 bits left in packet 81
[theora @ 0xb7f1a2f0]7 bits left in packet 82
Input #0, ogg, from 'Desktop/OneCube-DarkKnightSetup.ogv':
  Duration: 00:00:53.2, start: 0.333333, bitrate: 1879 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 3200x1200 [PAR 1:1 DAR 8:3], 24.00 tb(r)
Output #0, mpeg, to 'Desktop/OneCube-DarkKnightSetup.mpg':
    Stream #0.0: Video: mpeg1video, yuv420p, 3200x1200 [PAR 1:1 DAR 8:3], q=2-31, 200 kb/s, 24.00 tb(c)
Stream mapping:
  Stream #0.1 -> #0.0
[theora @ 0xb7f1a2f0]Theora bitstream version 30201
[theora @ 0xb7f1a2f0]560 bits left in packet 81
[theora @ 0xb7f1a2f0]7 bits left in packet 82
Press [q] to stop encoding
frame= 1285 fps= 20 q=1.6 Lsize=    6706kB time=53.5 bitrate=1026.8kbits/s    
video:6673kB audio:0kB global headers:0kB muxing overhead 0.496457%
jmap82@JMAP2:~$ 

```

I don't want to put an obnoxous amount of output into this post, so if you want to see more examples of what I'm seeing, I'll be gradually posting them here:  [http://jmap82.com/term-output]("http://jmap82.com/term-output")

Thanks again.

---

### Post by jmap82 on 2009-03-19
I'm continuing to test things.... but I continue to get the "Invalid codec type -1" error pretty much every time, and sometime the output file is OK and sometimes it isn't... it seams to be fickle, which isn't a nice color for computers.

---

### Post by jmap82 on 2009-03-19
Dangit!  I resign this post... Admin's feel free remove it.  I think the problem was that the resolution of my source video was too big for ffmpeg to handle.  Previously when I converted my 1920x1200 desktop recording session, it worked fine, and then the next time I tried to convert a video was after I updated and I tried to convert a 3200x1200 desktop recording session.  When it didn't work I attributted it to the update, and not my change in video resolution.

It is still annoying, but it isn't the problem I originally thought it was.

Sorry for the mix up, but thank you for your time.

1 more point for stupidity. :(

---

### Post by andrew.46 on 2009-03-19
Hi,

Well, it is good to hear that you have solved the problem to your satisfaction :-). If you continue to have an interest in FFmpeg one day search out the FakeOutdoorsman's guide on these forums and have a go at the svn FFmpeg: things will always work a little better with the fuller, more up to date version.

All the best,

Andrew

---

