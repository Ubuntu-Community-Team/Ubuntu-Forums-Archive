---
title: "ffmpeg and x264 'invalid width' error"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by SyvanX on 2007-01-08
I installed the latest svn of ffmpeg and x264 to encode for the video ipod.  At first ./configure wouldn't allow me to even --enable-x264 reporting that the (installed) requirements weren't met, so now it is able to find the requirements, but when I try to convert to an x264 video I get the following error.

```
ffmpeg -i /home/syvanx/InputTest.mpg -vcodec h264 -s 640x480 /home/syvanx/x264Test.mp4
FFmpeg version SVN-r7430, Copyright (c) 2000-2006 Fabrice Bellard, et al.
  configuration:  --prefix=/usr --enable-gpl --enable-mp3lame --enable-libogg --enable-vorbis --enable-faad --enable-faadbin --enable-libgsm --enable-xvid --enable-x264 --enable-a52 --enable-a52bin --enable-dts --enable-pp --enable-pthreads --enable-dc1394 --enable-shared --enable-faac --enable-swscaler
  libavutil version: 49.1.0
  libavcodec version: 51.28.0
  libavformat version: 51.7.0
  built on Jan  8 2007 13:31:50, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, mpeg, from '/home/syvanx/InputTest.mpg':
  Duration: 00:29:54.3, start: 0.289422, bitrate: 5190 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
File '/home/adam/x264Test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/home/syvanx/Test.mp4':
  Stream #0.0: Video: h264, yuv420p, 640x480, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
**x264 [error]: invalid width x height (0x640)**
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

I've done plenty of googling and checking the recent ffmpeg-user archives to no avail.  It looks unresolved.  I was wondering if anyone else has experience with this, or if I should just give up and re-compile the ubuntu supplied source?

EDIT:  I can encode just fine using the mpeg4 codec ( -vcodec mpeg4 ) with the same options.

Thanks in advance.

---

### Post by cor2y on 2007-01-24
yes i have the same error , but this is trying it with mencoder.
Looked via google as well and no results either.
Even with the -vf option in mencoder same error.
x264 requires 16x16 multiples resized and even that didn't work.

---

### Post by SyvanX on 2007-01-24
I was able to resolve this from the x264 mailing archives.  

[http://www.via.ecp.fr/via/ml/x264-devel/2007-01/msg00023.html](http://www.via.ecp.fr/via/ml/x264-devel/2007-01/msg00023.html)
and
[http://www.via.ecp.fr/via/ml/x264-devel/2007-01/msg00028.html](http://www.via.ecp.fr/via/ml/x264-devel/2007-01/msg00028.html)

The error was due to a bad symlink in libx264 from installing a new version of x264 on an old version of x264

run this, and see what the output is,

```
ls -l /usr/local/lib/ | grep libx264  # yours *might* be /usr/lib/
-rw-r--r-- 1 root root   731912 2007-01-22 09:39 libx264.a
lrwxrwxrwx 1 root root       13 2007-01-22 09:39 libx264.so -> libx264.so.54
-rwxr-xr-x 1 root root   676292 2007-01-22 09:39 libx264.so.54
```

Remove all libx264 files:

sudo rm /usr/local/lib/x264*

return to the x264 source directory and run:

```
make uninstall
make clean
make
make install
```

The problem seemed to be due to not uninstalling before installing the svn ffmpeg.  I just put holds on ffmpeg and x264 since i'm running svn versions of them and dpkg doesn't complain to me anymore.

That's what did it for me.  It won't transfer to my iPod, but that's a different story.

EDIT: I screwed up the above resolution the first time.

---

### Post by cor2y on 2007-01-26
ok i have been trying this over and over.

How do you get svn ffmpeg to recognze the svn version of x264, i never did compile my version with x264 before bevcause it would never recognize that x264 was istalled.
However using the version located in synaptic libx264-dev and it finds it with no problem.

---

### Post by SyvanX on 2007-01-26
I was having the exact same problem, if you look through the ffmpeg configure script, it includes this line:
> enabled x264    && [require]("http://src.opensolaris.org/source/raw/sfw/usr/src/cmd/bash/bash-3.0/examples/scripts.noah/require.bash") x264 x264.h x264_encoder_open -lx264

That makes sure you have all those requirements met otherwise ./configure will fail, which happened to me many times.  I don't remember at what point it officially worked for me, at one point I removed that line from configure, but it still broke on compiling. :( 

Try this config for x264 (with gpac installed):

```
./configure --enable-shared --enable-mp4-output --extra-ldflags=-L../gpac/bin/gcc
```

I think that --extra-ldflags argument was helpful for some reason.

---

### Post by cor2y on 2007-01-26
gpac and --enable-mp4-output continually failed when in make.
I didn't try pointing directly to gpac though i thought just having it installed via apt-get would be enough.
So now x264 is compiled without mp4 output.

As for the ffmpeg problem i got so frustrated i decided to use after make

> 
sudo checkinstall make install


And all of sudden ffmpeg could find x264 SVN go figure it needed to be a debian package, make install just wasn't enough although it was enough for mplayer/mencoder.

I will try to enable mp4-output and see how that goes.

---

### Post by cor2y on 2007-01-28
ok tried to compile  with gpac using the above configure.
got this error
> 
/usr/bin/ld: /usr/lib/gpac: No such file: File format not recognized
collect2: ld returned 1 exit status
make: *** [libx264.so.54] Error 1


don't know what i could be missing.

---

### Post by SyvanX on 2007-01-28
I'm sorry, are you compiling gpac, or x264 with --enable-mp4-output

if it's gpac I had some problems compiling just like that.

I used this procedure for gpac, with gpac_extra_libs
```

make clean
./configure
make lib
make apps
make install
```

---

### Post by cor2y on 2007-01-28
ok i see it was with x264 and --enable-mp4-output

i just took gpac from synaptic and didn't compile it neither did i add the extra libs.

---

