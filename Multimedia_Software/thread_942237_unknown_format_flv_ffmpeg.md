---
title: "unknown format: flv ffmpeg"
date: 2008-10-09
forum: Multimedia Software
---

### Post by ghostandmachine on 2008-10-09
I'm trying to convert a flv to mp3 with ffmpeg using the code below: 

```
ffmpeg -i video.flv song.mp3 
```

Now I've been able to do this in the past but I had to reinstall Hardy for a mishap.

I've also installed the repo of Medibuntu.

I'm getting the error "video.flv: unknown format" and I don't understand.

thanks in advance.

---

### Post by wolfen69 on 2008-10-09
do you have flash installed?

---

### Post by ghostandmachine on 2008-10-09
yes. I've installed the nonflash-plugin and the adobe flash 9 from their home page

---

### Post by FakeOutdoorsman on 2008-10-09
Give us your exact ffmpeg command and the full ffmpeg output.

---

### Post by ghostandmachine on 2008-10-09
```

eric@ubuntu-studio:~/Music$ ffmpeg -i video.flv jason_mraz-plane.mp3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
video.flv: Unknown format

```

I used youtube-dl to download the video if that helps.

---

### Post by FakeOutdoorsman on 2008-10-09
I've only seen this error when the input file is corrupt.  The is no reason why Medibuntu's ffmpeg can't do this.  Are you using an old version of youtube-dl?  Did you try to convert the video file that is stored in /tmp (if viewed in Firefox and with the browser still open if I remember correctly)?

---

### Post by ghostandmachine on 2008-10-09
downloaded the latest version of youtube-dl and redownloaded it. the conversion went fine. thanks.

---

### Post by FakeOutdoorsman on 2008-10-09
Eeeeexcellent.  If the flv audio is already mp3, you can just copy the audio stream instead of re-encoding:
```
ffmpeg -i input.flv -acodec copy ouput.mp3
```

---

### Post by gravityyy on 2010-03-10
Can someone help me with this:

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'video.flv':
  Duration: 00:05:10.54, start: 0.000000, bitrate: 329 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 249 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 80 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, avi, to 'test.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 320x240, q=2-31, 0 kb/s, 90k tbn, 29.92 tbc
    Stream #0.1: Audio: mp2, 441000 Hz, stereo, s16, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0

---

### Post by ron999 on 2010-03-10
..............................

---

