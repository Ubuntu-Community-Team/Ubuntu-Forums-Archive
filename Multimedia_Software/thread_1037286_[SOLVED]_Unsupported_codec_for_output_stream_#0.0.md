---
title: "[SOLVED] Unsupported codec for output stream #0.0"
date: 2009-01-11
forum: Multimedia Software
---

### Post by xjgnsdof on 2009-01-11
Ffmpeg has been working just fine, as has DownloadHelper for Firefox (which uses ffmpeg). Recently, I've been getting the following output in Terminal:

```
Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from '1.flv':
  Duration: 00:08:42.5, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 320x240 [PAR 0:1 DAR 0:1], 29.97 tb(r)
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, 64 kb/s
File '1.avi' already exists. Overwrite ? [y/N] y
Output #0, avi, to '1.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 320x240 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0

```

DownloadHelper also fails to convert flash video to AVI using ffmpeg.

What's wrong with ffmpeg on my machine?

---

### Post by FakeOutdoorsman on 2009-01-11
What is the command that is being passed on to ffmpeg?

---

### Post by xjgnsdof on 2009-01-11
> **FakeOutdoorsman said:**
> What is the command that is being passed on to ffmpeg?

I only know one command, which has always worked for me:

```
ffmpeg -i original.flv converted.avi
```

---

### Post by FakeOutdoorsman on 2009-01-11
Install the **libavcodec-unstripped-51** package.  This will enable ffmpeg support for mpeg4 encoding.

---

### Post by xjgnsdof on 2009-01-11
Awesome. That did that trick. I have to ask: after I updated my Intrepid systems a few days ago, why did I suddenly lose the ability to encode mpeg4 using ffmpeg? I doubt that I removed the package that you mentioned on two systems without knowing about it.

---

### Post by FakeOutdoorsman on 2009-01-12
This is a new package for Ubuntu as of 8.10.  The stock ffmpeg in the Ubuntu repositories does not support all restricted formats due to them not meeting the license requirements in the Ubuntu License Policy.  You have to manually install them, usually with the ubuntu-restricted-extras metapackage (which contains libavcodec-unstripped-51 among a bunch of other packages), or individually as you did.

With Ubuntu Hardy you had the choice of using the Medibuntu repository ffmpeg.  Medibuntu does not supply a ffmpeg for Intrepid probably because libavcodec-unstripped-51 does the job.  Alternatively you could compile ffmpeg yourself, which is what I usually do:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by markhu on 2011-06-10
I had a similar problem but it said, "Unsupported codec for output stream #0.1"

Panicked for awhile since I have newer distro "Ubuntu 10.04.2 LTS" and newer lib package "libavcodec-unstripped-52" but then I realized a subtle difference in the error message:

Unsupported codec for output stream #0.1
is not the same as 
Unsupported codec for output stream #0.0

Turns out there is some oddity with the AUDIO codecs (0 is video and 1 is audio) which I was able to overcome by specifying

 -acodec copy

Presumably that "copy" value could be replaced with the name of another codec, but I have not found one that works yet.

slightly more detailed paste:

Output #0, mov, to '101_0080-slim300k24fps.MOV':
    Stream #0.0(eng): Video: mpeg4, yuv420p, 848x480, q=2-31, 300 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1(eng): Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1

Unsupported codec for output stream #0.1

---

