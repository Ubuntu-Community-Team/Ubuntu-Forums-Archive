---
title: "ffmpeg - Can output to avi but not mpeg?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by khughitt on 2008-08-29
Hi all,

I'm just starting out with ffmpeg (installed version 3:0.cvs20070307-5ubuntu7.1+medibuntu1 via aptitude), and was wondering if someone could help me with some problems I'm having.

I am following some examples at [http://ffmpeg.mplayerhq.hu/faq.html#SEC14](http://ffmpeg.mplayerhq.hu/faq.html#SEC14). I would like to take a collection of .png images, and create a movie (either avi or mpeg to start with).

The example, however, does not work for me as is, and only works if I first convert the images to jpeg, and then output to .avi (mpeg doesn't work):
```

$ **ffmpeg -f image2 -i composite%d.jpg out.avi**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, image2, from 'composite%d.jpg':
  Duration: 00:00:00.0, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: mjpeg, yuvj420p, 1024x1024, 25.00 fps(r)
Output #0, avi, to 'out.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 1024x1024, q=2-31, 200 kb/s, 25.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    2 q=2.0 Lsize=      60kB time=0.1 bitrate=6129.0kbits/s    
video:54kB audio:0kB global headers:0kB muxing overhead 10.321117%

```

If I try to produce an mpeg movie the file is produced but a blank screen is displayed:

```
$ **ffmpeg -f image2 -i composite%d.jpg out.mpg**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, image2, from 'composite%d.jpg':
  Duration: 00:00:00.0, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: mjpeg, yuvj420p, 1024x1024, 25.00 fps(r)
Output #0, mpeg, to 'out.mpg':
  Stream #0.0: Video: mpeg1video, yuv420p, 1024x1024, q=2-31, 200 kb/s, 25.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=    2 q=2.0 Lsize=      60kB time=0.0 bitrate=12288.0kbits/s    
video:59kB audio:0kB global headers:0kB muxing overhead 1.733645%

```

Finally, I'm also having trouble using PNG images to produce either format:

```
**ffmpeg -f image2 -i composite%d.png out.avi**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[image2 @ 0xb7f37110]Could not find codec parameters (Video: png, 1024x1024)
composite%d.png: could not find codec parameters

```


Any suggestions? I've been looking through ffmpeg's documentation, but have not been able to find anything just yet.

Any help would be greatly appreciated.

Thanks!
Keith

---

### Post by eggdeng on 2008-08-29
You might want to look into Avidemux.
> Avidemux can also open a stream of uncompressed BMP files (RGB) or a set of JPEG files or a set of PNG files.
from [http://avidemux.org/admWiki/index.php?title=Input_formats]("http://avidemux.org/admWiki/index.php?title=Input_formats")

---

### Post by khughitt on 2008-09-03
Thanks for the suggestion. One of the advantages to using ffmpeg, however, is that there is a PHP module (ffmpeg-php) that makes it easy to manipulate videos on the fly in a web application.

Anyone else have experience with ffmpeg on Ubuntu?

Keith

---

### Post by FakeOutdoorsman on 2008-09-03
This worked for me:
```
ffmpeg -i seq%d.png output.mpg
```
Also worked with an avi output.  My png files were sequentially named seq1.png, seq40.png, etc.  FFmpeg gives the following info for one of the png files:
```
ffmpeg -i seq1.png
Input #0, image2, from 'seq1.png':
Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
Stream #0.0: Video: png, rgb24, 720x480, 25.00 tb(r)
```

---

### Post by khughitt on 2008-09-04
> **FakeOutdoorsman said:**
> This worked for me:
```
ffmpeg -i seq%d.png output.mpg
```
Also worked with an avi output.  My png files were sequentially named seq1.png, seq40.png, etc.  FFmpeg gives the following info for one of the png files:
```
ffmpeg -i seq1.png
Input #0, image2, from 'seq1.png':
Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
Stream #0.0: Video: png, rgb24, 720x480, 25.00 tb(r)
```


Hi FakeOutdoorsman,

Thanks for the reply. What version of Ubuntu and FFMpeg are you using?
I tried the same commands you used but got very different results. First of all, png images did not seem to be supported at all:

```
**$ffmpeg -i composite1.png**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[image2 @ 0xb7f8a110]Could not find codec parameters (Video: png, 1024x1024)
**composite1.png: could not find codec parameters**

```

Although jpeg files are recognized:
```

$ **ffmpeg -i composite1.jpg**
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, image2, from 'composite1.jpg':
  Duration: 00:00:00.0, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: mjpeg, yuvj420p, 1024x1024, 25.00 fps(r)
Must supply at least one output file

```

The video still ends up as blank when I try to use them to produce an *mpeg* movie. I have, however, been able to successfully produce avi, mp4, and flv movies using the jpeg images.

Any suggestions?

Thanks!

---

### Post by FakeOutdoorsman on 2008-09-04
I tried this with both a custom compiled SVN version of ffmpeg, and the same version you are using from Medibuntu.  I used ffmpeg to convert a dv movie to a png sequence, and then used those png images to test the command above.  Attach one of the png images.  The problem might be with them and not necessarily ffmpeg.

---

### Post by timcredible on 2008-09-04
ffmpeg supports mpeg.  you may want to use winff (gui front end for ffmpeg)

---

### Post by khughitt on 2008-09-05
> **FakeOutdoorsman said:**
> I tried this with both a custom compiled SVN version of ffmpeg, and the same version you are using from Medibuntu.  I used ffmpeg to convert a dv movie to a png sequence, and then used those png images to test the command above.  Attach one of the png images.  The problem might be with them and not necessarily ffmpeg.

I've attached one of the images I'm using. Any ideas?

---

### Post by FakeOutdoorsman on 2008-09-05
I get the same error as you.  The "file composite2.png" command shows your png as a 16-bit/color RGB image, but mine was 8-bit.  I'm guessing that ffmpeg can't handle 16-bit png.  I got it to work once I used the "convert" command (from imagemagick package) to convert from 16-bit to 8-bit:
```
convert composite2.png -depth 8 composite2b.png
```
Now turn it into a batch (this will overwrite existing files):
```
find ~/path -name '*.png' -exec convert {} -depth 8 {} \;
```

---

### Post by khughitt on 2008-09-07
> **FakeOutdoorsman said:**
> I get the same error as you.  The "file composite2.png" command shows your png as a 16-bit/color RGB image, but mine was 8-bit.  I'm guessing that ffmpeg can't handle 16-bit png.  I got it to work once I used the "convert" command (from imagemagick package) to convert from 16-bit to 8-bit:
```
convert composite2.png -depth 8 composite2b.png
```
Now turn it into a batch (this will overwrite existing files):
```
find ~/path -name '*.png' -exec convert {} -depth 8 {} \;
```

Thanks FakeOutdoorsman! :D

---

