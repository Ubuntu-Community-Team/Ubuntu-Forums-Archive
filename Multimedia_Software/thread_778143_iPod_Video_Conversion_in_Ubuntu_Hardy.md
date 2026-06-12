---
title: "iPod Video Conversion in Ubuntu Hardy"
date: 2008-05-01
forum: Multimedia Software
---

### Post by spo0neybard on 2008-05-01
I've read a bunch of things like 'scripts for iPod
video conversion' but it ends up I get a bunch of
'libfaac' errors and 'aac' codec errors. I don't know
what to do with that. I've tried winff and just the standalone
ffmpeg command line, but nothing works. Everything seems
to be scripted for ubuntu gutsy and below. Anyway if anyone can help,
that'd be great.

---

### Post by spo0neybard on 2008-05-06
This is a method for ipod converting in hardy.
Ok, I found out how to make the 'aac' thing work.
Ok if I use any program terms, google them up. Also
if there is an easier way, please tell me.
Essentials: Mencoder, VLC, Ffmpeg, Winff (Optional)

1. Open up a terminal.
2. cd to the directory that has the video file.
3. put this in the terminal:
```
mencoder input.wmv -o video.h264 -of rawvideo -ovc x264 -x264encopts crf=24:frameref=5:bframes=1:me=umh:partitions=all:trellis=1:qp_step=4:qcomp=0.7:direct_pred=auto:keyint=300 -vf scale=-10:-1,harddup -nosound -ofps 30000/1001
```
4. Once that's done you will see a video.h264 video file in the directory.
Don't touch it.
5. Enter this in the terminal:
```
mencoder input.wmv -o audio.aac -of rawaudio -ovc raw -oac faac -faacopts br=192:mpeg=4:object=2 -channels 2 -srate 48000
```
6. You will see a audio.aac file. This is the thing you need to convert.
7. Open up your handy dandy VLC player.
8. File > Open File
9. Browse for the _AUDIO_ file. (audio.aac)
10. Check Stream/Save In Advanced Options.
11. Click settings.
12. Check File and put down audio.mp3.
13. Encapsulation Method: MP4
14. Audio codec: check and put down MP3.
15. Click Ok.
16. Click Ok on the Open... box and it will start converting your audio.
17. When it is done converting change the name to audio.mp3
18. Open up a terminal and cd to the directory the audio (the thing you just converted) and the video (You should have it) are at.
19. Put this in the terminal:
20. ```
MP4Box output.mp4 -new -fps 29.97 -add audio.mp3 -add video.h264
```
21. This should make an output.mp4 file.
22. Convert the output.mp4 file with winff and your ready to go!
Btw if you have an ipod classic you should first change the video
size to 320-by-240.

---

### Post by dentaku65 on 2008-05-06
I suggest pytube (not really in topic here, but interesting); this is great sw capable to download from youtube save and convert for ipod video (and many other formats); here the link:

[http://bashterritory.com/pytube/index.php?option=com_content&task=view&id=14&Itemid=29]("http://bashterritory.com/pytube/index.php?option=com_content&task=view&id=14&Itemid=29")

deb pkg is available on the site but not in the repos.
Worth a try.

---

### Post by spo0neybard on 2008-05-06
Yeah, but  that was the problem.
That didn't work either. They both
run on ffmpeg, and ffmpeg was causing
the error.

---

### Post by dentaku65 on 2008-05-07
What about of this?

```
ffmpeg -vcodec xvid -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i file-of-input.avi -s 320x240 -aspect 4:3 file-of-output.mp4
```

:popcorn:

---

### Post by spo0neybard on 2008-05-07
Nope.

```
spartan117@spartan117:~/Desktop$ ffmpeg -vcodec xvid -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i 01.mp4 -s 320x240 -aspect 4:3 04.mp4FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
[aac @ 0xb7ec39a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '01.mp4':
  Duration: 00:03:33.6, start: 0.000000, bitrate: 498 kb/s
  Stream #0.0(und): Audio: aac
  Stream #0.1(und): Video: h264, yuv420p, 480x352, 29.97 fps(r)
Output #0, mp4, to '04.mp4':
  Stream #0.0: Video: xvid, yuv420p, 320x240, q=3-5, 0 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 0 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[aac @ 0xb7ec39a8]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Oh, by the way is there any way to merge together two mp4's together?

---

### Post by dentaku65 on 2008-05-09
I think my version of ffmpeg is the one the one from Medibuntu repository and it works; try to remove the one you have and install this one.

---

### Post by spo0neybard on 2008-05-09
I already have the medibuntu version.
I think the 'aac' codec thingy comes
already installed in feisty but not hardy.

---

### Post by Spenser_Gilliland on 2008-05-12
I'm having the same issue. 
spenser@myth:/var/lib/mythtv/videos/Video$ ffmpeg -i Family\ Guy\ -\ S5E01\ -\ Stewie\ Loves\ Lois.avi -acodec libfaac -ab 160k -s 640x480 -vcodec libx264 -b 1500kb -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me umh -subq 6 -trellis 1 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 1500kb -maxrate 1500kb -bufsize 2000kb -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 OUTPUT.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'Family Guy - S5E01 - Stewie Loves Lois.avi':
  Duration: 00:21:26.5, start: 0.000000, bitrate: 1141 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Unknown codec 'libfaac'

---

### Post by dentaku65 on 2008-05-13
> **Spenser_Gilliland said:**
> I'm having the same issue. 
spenser@myth:/var/lib/mythtv/videos/Video$ ffmpeg -i Family\ Guy\ -\ S5E01\ -\ Stewie\ Loves\ Lois.avi -acodec libfaac -ab 160k -s 640x480 -vcodec libx264 -b 1500kb -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -me umh -subq 6 -trellis 1 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt 1500kb -maxrate 1500kb -bufsize 2000kb -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 OUTPUT.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'Family Guy - S5E01 - Stewie Loves Lois.avi':
  Duration: 00:21:26.5, start: 0.000000, bitrate: 1141 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 160 kb/s
Unknown codec 'libfaac'

Is correct, the option must be:
**-acodec aac**
and not
[B]-acodec libfaac
[/B]

---

### Post by crobinson55331 on 2008-05-13
I am successfully using the HandbrakeCLI from the command line, but it also uses ffmpeg library.  I have used it successfully on both DVD's and recorded television shows.  Conversion is very slow even with a powerful processor so I just set it to run at night.  Follow the instructions at [http://handbrake.fr/](http://handbrake.fr/)

---

