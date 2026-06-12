---
title: "flv in ffmpeg stopped working with intrepid"
date: 2008-11-30
forum: Multimedia Software
---

### Post by lykwydchykyn on 2008-11-30
Since upgrading to Intrepid, I cannot seem to play flv (flash video files) of any kind.  Particularly, i have a script that converts flv files using ffmpeg.  When I try to use it, or when I try to play flv in mplayer, I get an error that the file format is unsupported.

I notice in the past the conventional wisdom was to install ffmpeg from medibuntu, but there is no ffmpeg for intrepid in medibuntu.  So now what?  I've searched the repos for anything related to flv.

EDIT: i have the medibuntu version of mplayer installed, but it does not play flv.  Interestingly, I can play flash video in firefox (via flashplugin).

---

### Post by andrew.46 on 2008-11-30
Hi,

Can I direct you to 2 guides on these forums? For the svn mplayer:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

and for ffmpeg:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Both of the gentlemen who run these threads are keen, knowledgeable and approachable :-).

  Andrew

---

### Post by lykwydchykyn on 2008-11-30
Ok, so do I need to do this to get .flv working?  Is there some known issue? 

Before I go to the trouble of recompiling everything, can anyone take 10 seconds to try to play a .flv file in Intrepid, and maybe tell me if it works for them or not?

---

### Post by FakeOutdoorsman on 2008-11-30
> **lykwydchykyn said:**
> Particularly, i have a script that converts flv files using ffmpeg.  When I try to use it, or when I try to play flv in mplayer, I get an error that the file format is unsupported.
Paste your ffmpeg command and the full ffmpeg output.
> **andrew.46 said:**
> 
Both of the gentlemen who run these threads are keen, knowledgeable and approachable :-).

  Andrew
Thanks for the kind words, Andrew.

---

### Post by lykwydchykyn on 2008-11-30
if I do this:
```

ffmpeg -i test.flv

```

I get the following output:
```

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
[flv @ 0xb7f61388]Unsupported video codec (7)
[flv @ 0xb7f61388]Unsupported audio codec (a)
[flv @ 0xb7f61388]Unsupported video codec (7)
[flv @ 0xb7f61388]Unsupported video codec (7)

```
The last error line repeats ad infinitum.

i get similar output from trying to play the file in mplayer, or trying other tasks with ffmpeg.

I've tried purging and reinstalling mplayer and ffmpeg.

---

### Post by FakeOutdoorsman on 2008-12-04
I was able to replicate your error, but I was unable to figure out why it does that because it should be able to support the codecs usually used in flv.  Using a self compiled recent version of ffmpeg had no issues though.  More info:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by lykwydchykyn on 2008-12-04
I've been testing more and it's not consistent.  I'm mainly having problems with videos I download from youtube by extracting them from my cache.  I'm suspecting that youtube may have modified its video format to prevent this sort of thing.

Even so, I found a workaround is to use clive to get these files and download them.

Now if I can only work around the fullscreen video bug I've been dealing with...

---

### Post by sayakb on 2008-12-04
Why not try VLC?
```
sudo apt-get install vlc
```

Esp, as it shifted to QT4

---

### Post by FakeOutdoorsman on 2008-12-04
> **lykwydchykyn said:**
> I'm suspecting that youtube may have modified its video format to prevent this sort of thing.
Youtube recently moved some or all content to h264 video with stereo aac audio:
```
Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 29.42 tb(r)
Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
```
Previously they were using Sorensen Spark h263 with mono mp3 audio:
```
Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```
I can convert with self-compiled ffmpeg and play the new Youtube h264 videos just fine from the /tmp cache.  If the cache videos are giving you trouble, then check out the [youtube-dl]("http://www.arrakis.es/~rggi3/youtube-dl/") script.

---

### Post by lykwydchykyn on 2008-12-04
@LinuxIsInnovation: I have, same results.  VLC crashes my laptop most of the time anyway, thanks to a bug somewhere in xorg with my video card.

@FakeOutdoorsman:  That explains it then.  clive seems to work, straight from the repos, strangely enough.  If I get up the gumption to do some more compiling, I might give that a shot.

---

### Post by Alfred_McGee on 2008-12-11
Solved lykwydchykyn's problem on my own computer by following the link posted above by FakeOutdoorsman. It's the howto on compiling ffmpeg from source.

---

