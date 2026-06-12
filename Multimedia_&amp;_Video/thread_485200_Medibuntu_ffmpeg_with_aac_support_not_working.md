---
title: "Medibuntu ffmpeg with aac support not working?"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by tlianza on 2007-06-26
Hi All,

I was trying to follow [this guide]("https://help.ubuntu.com/community/iPodVideoEncoding") and it says that for Feisty users we can download the Medibuntu version of ffmpeg and get aac support without compiling ffmpeg from source.

I did that, and yet I still don't seem to have aac support.  When I try to encode a video with aac audio, this is what I see (emphasis mine, obviously):

ffmpeg -i /video/recordings/1060_20070625230000.mpg -vcodec mpeg4 -acodec aac test.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin **--enable-faad --enable-faac** --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 25 2007 22:39:13, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, mpeg, from '/video/recordings/1060_20070625230000.mpg':
  Duration: 00:27:42.3, start: 0.291389, bitrate: 5147 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
**Unknown codec 'aac'**

So, I get the "Unknown codec 'aac'" error, but then right above it I can see --enable-faad and --enable-faac in the configuration.  Any ideas about what's going on?

Thanks!
Tom

---

### Post by tlianza on 2007-06-27
Ah... figured it out.  I needed to install libavcodec0d as well.  That seems to have grabbed the aac codec I was missing.  I hope this helps someone.

sudo apt-get install libavcodec0d

---

### Post by TutoWRM on 2007-06-28
dude you just saved me..... i couldn't get rid of the acc error, but with the sumple install libavc.... and everything worked out, many many thanks :D
i'm gonna post this in my blog, because i've read that many people got the same problem :)

---

### Post by satx on 2007-06-28
Test

---

### Post by skooter on 2007-07-08
Hmm... Didn't help me... 

```
FFmpeg version SVN-r9533, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-liba52 --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264
  libavutil version: 49.4.1
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jul  8 2007 10:37:22, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, mpeg, from '/var/lib/mythtv/recordings/2001_20070708001000.mpg':
  Duration: 00:35:57.3, start: 0.276111, bitrate: 5340 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480, 6000 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 384 kb/s
Unknown codec 'aac'
```

And ...
```
sudo apt-get install libavcodec0d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec0d is already the newest version.
```

---

### Post by eyemou on 2007-07-09
I'm having the same problem, it seems. I have tried installing ffmpeg from both medibuntu and the SVN source, and always receive the "unknown codec 'aac'" error message when it comes time to encode.

I have aac installed, and as you can see from the ouput below, ffmpeg sees it as "enabled".

Here's the output, I get... Any help/insight appreciated.

FFmpeg version SVN-r9569, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-liba52 --enable-dc1394 -           -enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enabl           e-libx264
  libavutil version: 49.4.1
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jul  9 2007 22:15:47, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, mpeg, from '/home/rich/clip3.mpeg':
  Duration: 00:00:59.8, start: 0.446022, bitrate: 1170 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x288, 1000 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 128 kb/s
Unknown codec 'aac'
Encode step FAILED:  ffmpeg -y -i "/home/rich/images/clip3.mpeg" -f mp4 -pass 2 -subq 6 -threads 1 -v            1 -vcodec h264 -b 200k -bt 175k -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb           8x8 1 -brdo 1 -me_range 21 -chroma 1 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^           (1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -b_qfactor 0.76923078 -maxrate 1500k -bufsize 2           44k -cmp 1 -s 294x240 -acodec aac -ab 96k -ar 48000 -ac 2  -map 0.0  -map 0.1  ".tmp.mp4"


I realize that this has been a popular topic, but nothing has helped so far. I do have libavcodec0, and the dev version, installed as well.

---

### Post by alexxmed on 2007-07-31
simple RTFM: new call for aac support is

 -acodec libfaac


(searching 4 day in internet but 5' of reading faq.texi resolving)

not probed, i'm yet compiling....

:)

---

### Post by alexxmed on 2007-07-31
from faq.texi:

@section How do I encode videos which play on the iPod?

@table @option
@item needed stuff
-acodec libfaac -vcodec mpeg4 width<=320 height<=240
@item working stuff
4mv, title
@item non-working stuff
B-frames
@item example command line
ffmpeg -i input -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X output.mp4
@end table

---

### Post by reaganf2 on 2008-05-18
can't seem to be able to find this package (libavcodec0d) in hardy...
is there any workaround...?? having the same problem...

---

### Post by TylerRick on 2008-05-19
> **reaganf2 said:**
> can't seem to be able to find this package (libavcodec0d) in hardy...is there any workaround...?? having the same problem...

I started having this problem too, as soon as I upraded to hardy.

I believe you actually want the newer version, **libavcodec1d**, rather than **libavcodec0d**.

The way I got aac encoding working again in ffmpeg was first to add these lines to the top of **/etc/apt/sources.list**:

```

deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```

and then:

```

sudo apt-get update && sudo apt-get install medibuntu-keyring
sudo apt-get remove ffmpeg
sudo apt-get install ffmpeg
sudo apt-get install libavcodec1d
```

Good luck!

---

### Post by vociferous666 on 2008-05-22
im having a problem with stepmania breaking my package manager because i forced the install even though libavcodec0d wasnt installed rather libavcodec1d was installed.
how do i get stepmania to resolve its dependency to libavcodec1d?

---

### Post by TylerRick on 2008-05-22
I'm not really sure... Maybe try contacting the maintainer of StepMania and asking them to use more up-to-date dependencies?

---

