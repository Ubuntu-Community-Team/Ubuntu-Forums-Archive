---
title: "[SOLVED] Code required to convert flv to ogv"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Rytron on 2008-11-12
Hi,
I need some mencoder code to convert an flv file to an ogv file.
Alternatively an ffmpeg line of code would also suffice.

---

### Post by Rytron on 2008-11-30
Anyone?

---

### Post by FakeOutdoorsman on 2008-11-30
This should do it:
```
ffmpeg -i input.flv -acodec vorbis -ac 2 -vcodec libtheora -f ogg output.ogv
```
If it doesn't work then show the full ffmpeg output.

---

### Post by Rytron on 2008-12-01
> **FakeOutdoorsman said:**
> This should do it:
```
ffmpeg -i input.flv -acodec vorbis -ac 2 -vcodec libtheora -f ogg output.ogv
```
If it doesn't work then show the full ffmpeg output.

Hi,
It worked on 2 flv files perfectly. On a third flv file I got this:

```
:~/Desktop$ ffmpeg -i input.flv -acodec vorbis -ac 2 -vcodec libtheora -f ogg output.ogv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, flv, from 'input.flv':
  Duration: 00:08:16.0, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x238 [PAR 0:1 DAR 0:1], 24.00 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Output #0, ogg, to 'output.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 320x238 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 24.00 tb(c)
    Stream #0.1: Audio: vorbis, 22050 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault
username@Tron1:~/Desktop$ ffmpeg -i input.flv -acodec vorbis -ac 2 -vcodec libtheora -f ogg output.ogv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, flv, from 'input.flv':
  Duration: 00:08:16.0, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x238 [PAR 0:1 DAR 0:1], 24.00 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Output #0, ogg, to 'output.ogv':
    Stream #0.0: Video: libtheora, yuv420p, 320x238 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 24.00 tb(c)
    Stream #0.1: Audio: vorbis, 22050 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault
```

---

### Post by FakeOutdoorsman on 2008-12-01
I can confirm this error using Intrepid's ffmpeg with and without the "unstripped" libraries with flv files that use h264 video and aac audio.  I couldn't get it to work with these versions, but it does work fine using a recent version of ffmpeg that I compiled myself.  If you want to compile ffmpeg, then you can check out my guide:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by Rytron on 2008-12-02
> **FakeOutdoorsman said:**
> I can confirm this error using Intrepid's ffmpeg with and without the "unstripped" libraries with flv files that use h264 video and aac audio.  I couldn't get it to work with these versions, but it does work fine using a recent version of ffmpeg that I compiled myself.  If you want to compile ffmpeg, then you can check out my guide:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

Cheers FakeOutdoorsman, you really know your stuff.
Do you know of a code line that can be used with mencoder for converting flv to ogv? Mencoder seems to have less problems with versions than ffmpeg.

---

### Post by FakeOutdoorsman on 2008-12-02
> **Rytron said:**
> Cheers FakeOutdoorsman, you really know your stuff.
Do you know of a code line that can be used with mencoder for converting flv to ogv? Mencoder seems to have less problems with versions than ffmpeg.
Many of the ffmpeg problems come from Ubuntu using an old revision.  I'm not very familiar with mencoder, but I'm sure andrew.46 can point you in the right direction.  Try asking him through this thread:
[[Howto] Successfully install the svn mplayer + gmplayer + all the codecs]("http://ubuntuforums.org/showthread.php?t=558538")

---

### Post by Rytron on 2008-12-14
> **FakeOutdoorsman said:**
> This should do it:
```
ffmpeg -i input.flv -acodec vorbis -ac 2 -vcodec libtheora -f ogg output.ogv
```
If it doesn't work then show the full ffmpeg output.

I'll use your code firstly. If that fails then I'll use OggConvert.

---

### Post by andrew.46 on 2008-12-27
Hi Rytron,

Good to hear from you again! As far as I am aware MPlayer will play ogv files but Mencoder will not encode to this format. Hopefully somebody will correct me if this is horribly wrong. 

Andrew

---

### Post by andrew.46 on 2008-12-27
Hi,

Well, never one to leave well enough alone I had a good look at ffmpeg2theora in an attempt to duplicate the results achieved by Fakeoutdoorsman. ffmpeg2theora uses ffmpeg so results should be the same but hopefully a little easier on the commandline :-).

Picked up a flash video from youtube:

```
youtube-dl -o test.flv http://www.youtube.com/watch?v=EwL0G9wK8j4
```

which comes as:

```
Stream #0.0: Video: flv, yuv420p, 320x240, 29.92 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 112 kb/s
```

Conversion to ogv as follows:

```
$ ffmpeg2theora -V 200 -A 64 test.flv
```

was trouble free but I noticed an odd 'phantom' stream that I do not fully understand:

```
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 320x240, 29.92 tb(r)
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, s16, 64 kb/s
```

Any ideas on what the extra Stream #0.0 is all about? And I will admit that I still suspect that the svn ffmpeg is the way to go :-).

Andrew

**Edit:** Found the ffmpeg2theora mailing list and posted a query there: [http://mail.kein.org/pipermail/ffmpeg2theora/2008-December/000021.html](http://mail.kein.org/pipermail/ffmpeg2theora/2008-December/000021.html)

---

### Post by Rytron on 2009-01-02
```
$ ffmpeg2theora -V 200 -A 64 test.flv
```

This does the job. Cheers.

---

### Post by ssavelan on 2009-01-24
> **Rytron said:**
> Hi,
I need some mencoder code to convert an flv file to an ogv file.
Alternatively an ffmpeg line of code would also suffice.

How about going the other way?  ie ogv to flv?

---

### Post by FakeOutdoorsman on 2009-01-26
> **ssavelan said:**
> How about going the other way?  ie ogv to flv?
```
ffmpeg -i input.ogv -ar 44100 -acodec libmp3lame output.flv
```
Make sure to install the **libavcodec-unstripped-51** package to enable restricted encoders such as libmp3lame.

---

