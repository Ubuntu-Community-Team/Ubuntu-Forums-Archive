---
title: "MP4 not playing"
date: 2009-02-15
forum: Multimedia Software
---

### Post by duott on 2009-02-15
I've just bought Samsung i8510 smartphone and shot a couple of vids. They're in MP4 format and the model suggests that the video codec is DivX (no idea about the audio though). 

The problem is, 
* VLC plays it with no sound
* the same with Totem
* Mplayer plays the sound but fails to render the video properly
* Avidemux says it cannot find the appropriate audio codec

What can I do to get both video and audio working in these vids?

Thanks.

---

### Post by hansdown on 2009-02-15
Hi duott.

Do you have ffmeg installed from synaptic?

---

### Post by duott on 2009-02-16
thanks for reply.

yes, apt says the latest version of ffmpeg is installed. 

[upd] it turned out that the problem is the **AMR audio codec**. Solutions on this forum suggest installing amrng from medibuntu repos, i did that but it still didn't help.

---

### Post by wolfen69 on 2009-02-16
```
sudo apt-get install libavcodec51
```

---

### Post by hansdown on 2009-02-16
If you go to synaptic package manager, search for ```
gstreamer
```. You need  ```
gstreamer0.10-ffmpeg
```

It doesn't hurt to install any gstreamer plugins you see.

---

### Post by wolfen69 on 2009-02-16
you could also try installing the gstreamer good and ugly plugins.

---

### Post by duott on 2009-02-16
I have all these packages installed, no good. 

Besides, i spent several hours trying to compile libamrnb, ffmpeg and vlc with amr support. Got totally confused by now.

Some posts around here also suggested realplayer, which didn't work either.

I was going to shoot a lot of vids so I really need them playable... :(

---

### Post by andrew.46 on 2009-02-17
Hi,

Just make sure that these files really have amr sound first. FFmpeg will do this for you:

```
ffmpeg -i myfile.mp4
```

Can you post the results here? If they are definitely amr files you could try [this MPlayer guide]("http://ubuntuforums.org/showthread.php?t=1024592") which features amr support.

Andrew

---

### Post by duott on 2009-02-17
Here is the output.

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 300.00 (300/1) -> 30.00 (30/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '2009-02-15-04.mp4':
  Duration: 00:00:47.0, start: 0.000000, bitrate: 687 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    Stream #0.1(und): Audio: samr / 0x726D6173, 8000 Hz, mono
Must supply at least one output file
```

As i wrote above, mplayer has sound, but fails to render the video properly (the image like.. (jitters?), becomes too slow and then too fast). I'll try to enable glx and select opengl in mplayer, maybe that will work.

---

### Post by andrew.46 on 2009-02-17
Hi,

Seems a little odd. Can you post the file somewhere?

Andrew

---

### Post by duott on 2009-02-17
OK, shot an example:

[http://rapidshare.com/files/199374360/vid4.mp4.html](http://rapidshare.com/files/199374360/vid4.mp4.html)

upd. got glx working and changed mplayer video driver to opengl. Still having the same problem.

---

### Post by mc4man on 2009-02-17
You might want to try a newer version of mplayer.

As far as vlc, using the 8.10 default of 0.9.4, if you have the unstripped version of libavcodec51 installed then no sound. If you install the regular libavcodec51 (which is a stripped ver. ) then there is sound. 
Weird, usually the other way around.

That's what I see, only caveats are I also have very recent libavcodec52 installed (nothing stripped), but I'm very sure vlc 0.9.4 doesn't use it, and I'm on 32 bit install ( shouldn't matter with vlc

---

### Post by duott on 2009-02-17
**mc4man**
checked, i'm getting no sound with either of libavcodec51 packages installed. 

**_Partially solved_**: 

when I convert my files with the command
```
 mencoder "vid4.mp4" -o "movie.avi" -of lavf -oac pcm -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -ofps 24
```
i get an avi file which plays with both video and audio! 

but still, i'm wondering if there is a workaround to play them without conversion.

---

### Post by andrew.46 on 2009-02-18
Hi duott,

> **duott said:**
> OK, shot an example:

[http://rapidshare.com/files/199374360/vid4.mp4.html](http://rapidshare.com/files/199374360/vid4.mp4.html)


Thanks for that. However with the svn MPlayer, FFplay and vlc 0.9.8a there are no problems playing this file which FFmpeg identifies as:

```
Duration: 00:00:20.80, start: 0.000000, bitrate: 550 kb/s
Stream #0.0(und): Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 30.00 tb(r)
Stream #0.1(und): Audio: libamr_nb, 8000 Hz, mono, s16
```

Perhaps, as mc4man has suggested, a newer version of MPlayer might be a solution?

Andrew

---

### Post by mc4man on 2009-02-18
i think your best bet for mplayer if you don't wish to build would be to add the rvm ppa (smplayer ) to your sources and get a much newer version of mplayer and smplayer if desired. (He has a amd 64 build

[https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa)

As far as vlc it would be interesting if someone with a stock install could try your file. I'm starting to think vlc can't play back amr audio unless it's compiled with a ffmpeg (and libs) where amr support is enabled. (eliminating ubuntu's version

I never used the 0.9.4 before tonight, installed just to test your file. ( I use a 1.0 ver.that I build every 2 weeks to ck. progress 
That may account for why it would play and then not play as noted above ( don't understand why I could at all really.

On a tester, the file's audio would not play in vlc 0.9.4 nor in a 0.9.8a deb I found in launchpad for intrepid ( if your going to use a 0.9.x version 0.9.8a is far better

[https://launchpad.net/~smaioli/+archive/ppa](https://launchpad.net/~smaioli/+archive/ppa)

(small note - overall vlc 0.9.x is considered 'broken' in many area's, the 1.0's have made some progress.

---

### Post by duott on 2009-02-18
Thanks guys.

>Perhaps, as mc4man has suggested, a newer version of MPlayer might be a solution?

Weird stuff. Actually, after I installed mplayer from the launchpad repo above, it started to play the video OK, but the audio disappeared just as in VLC and Totem, and besides mencoder now cannot find the audio codec to convert the files to avi:

```
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'libamr_nb' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x726D6173.
```

I'll try SVN version later.

---

### Post by duott on 2009-02-18
The SVN version of MPlayer failed to build on make stage.

```
libx264.c: In function 'X264_init':
libx264.c:167: error: 'x264_param_t' has no member named 'i_bframe_adaptive'
make[1]: *** [libx264.o] Error 1
make[1]: Leaving directory `/home/duott/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
```

To sum it up:

[b]* Mplayer from standard Intrepid repos plays the audio, but fails on video;
* Mplayer from launchpad plays video, but fails on audio.[/b]

Now I need to merge these somehow x_x

---

### Post by andrew.46 on 2009-02-18
Hi duott,

> **duott said:**
> ```
libx264.c: In function 'X264_init':
libx264.c:167: error: 'x264_param_t' has no member named 'i_bframe_adaptive'
make[1]: *** [libx264.o] Error 1
make[1]: Leaving directory `/home/duott/mplayer/libavcodec'
make: *** [libavcodec/libavcodec.a] &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 2
```

This means you have an aged version of x264 somewhere on your system. Hunt it out, install a new copy from git and try again.

Andrew

---

### Post by rvm4000 on 2009-02-18
> **duott said:**
> *** Mplayer from launchpad plays video, but fails on audio.**

The packages in [https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa) are compiled without support for libamr.

---

### Post by duott on 2009-02-18
**rvm4000**,

any suggestions how can I recompile them 
with this support?

---

### Post by duott on 2009-02-18
**andrew.46**,

> This means you have an aged version of x264 somewhere on your system. Hunt it out, install a new copy from git and try again.

OK, I did that and was finally able to compile Mplayer from SVN. Libamr seems to work, got sound, but now it has no video output at all (that's even worse than the default Intrepid Mplayer troubled output) :(

I also compiled SMplayer from SVN just in case, and it gives the same troubled video output as the default Mplayer.

It's clearly possible to make Mplayer work somehow, because there was the launchpad package which did the video, but not the audio, and others which do it visa versa. If only I knew how to compile it to get both :(

---

### Post by rvm4000 on 2009-02-18
Probably you don't have installed some development packages.

The following should install all necessary build dependencies:
```

sudo apt-get build-dep mplayer

```

If you want to create deb packages, like the ones in launchpad, this document explains it:
[http://smplayer.berlios.de/forums/viewtopic.php?pid=3064#p3064](http://smplayer.berlios.de/forums/viewtopic.php?pid=3064#p3064)

Although maybe the easiest would be to recompile the sources of the packages in launchpad:

```

wget http://ppa.launchpad.net/rvm/ppa/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc2svn28403-0intrepid1.dsc
wget http://ppa.launchpad.net/rvm/ppa/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc2svn28403-0intrepid1.diff.gz
wget http://ppa.launchpad.net/rvm/ppa/ubuntu/pool/main/m/mplayer/mplayer_1.0~rc2svn28403.orig.tar.gz

dpkg-source -x mplayer_1.0~rc2svn28403-0intrepid1.dsc

cd mplayer-1.0~rc2svn28403
debuild

```

Just be sure you have also libamrnb-dev and libamrwb-dev installed before compiling.

---

### Post by duott on 2009-02-19
OK, I grew pretty tired of this one and, since I really need it, I did it a bit radical way: installed Debian Sid - and lo! - everything works out of the box!

Marking this thread as [SOLVED]. Thank you guys anyway :D

---

