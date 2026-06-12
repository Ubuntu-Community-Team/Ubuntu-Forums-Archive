---
title: "Video cutter with commandline ?"
date: 2010-02-19
forum: Multimedia Software
---

### Post by AnotherNoob on 2010-02-19
I m looking for a video cutter that cut a portion of video in the given format, i tried ffmpeg and avidemux but they touch( some modification) the original video so output doesn't remains same as the source 

is there any software for ubuntu 8.04 hardy which cuts the video portion as it is and have command line support 

Thanks for any help

---

### Post by FakeOutdoorsman on 2010-02-19
> **AnotherNoob said:**
> i tried ffmpeg and avidemux but they touch( some modification) the original video so output doesn't remains same as the source

FFmpeg is still your best bet here.  What was the command that you used?  FFmpeg can be used to trim a video without re-encoding.  For example, I have a video that is 50 seconds in duration.  I want my output video to be 30 seconds long, but I want to skip the first 15 seconds of the input video.  I also don't want to re-encode anything so I'll just copy the video and audio streams.  My command would look like:
```
ffmpeg -ss 15 -t 30 -i input.mkv -acodec copy -vcodec copy output.mkv
```

---

### Post by AnotherNoob on 2010-02-19
thanks for help, one more question may it work with all other formats other than mkv 


or i have to install codecs ? please tell me how i can install all major needed codecs, because my ffmpeg is not working with mkv format :(

thanks

---

### Post by FakeOutdoorsman on 2010-02-19
> **AnotherNoob said:**
> thanks for help, one more question may it work with all other formats other than mkv
It should work with any supported format.  I just used MKV as an example.

> **AnotherNoob said:**
> or i have to install codecs ? please tell me how i can install all major needed codecs, because my ffmpeg is not working with mkv format :(
It's not working?  Can you show your FFmpeg command and the complete output?  I think stock FFmpeg from the repository can copy streams without the need for installing the missing encoders, but it has been a long time since I've tested this.

You have two choices if you want to enable these missing encoders in Ubuntu 8.04:  install FFmpeg from Medibuntu, or compile FFmpeg.  Compiling has the advantage of using a recent FFmpeg with more bug fixes and enhancements, but there are a few more steps involved for installation.  Both options are listed here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by AnotherNoob on 2010-02-19
please take a look


```
$ ffmpeg -ss 15 -t 300 -i 1.mkv -acodec copy -vcodec copy 2.mkv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
[matroska @ 0xb7776110]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0xb7776110]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0xb7776110]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb7776110]Unknown entry 0x73a4 in info header
[matroska @ 0xb7776110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x55aa - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x23314f - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0x55ee - ignoring
[matroska @ 0xb7776110]Unknown track header entry 0xaa - ignoring
[matroska @ 0xb7776110]Unknown entry 0x93 in cluster data
[matroska @ 0xb7776110]Read error at pos. 650 (0x28a)
1.mkv: could not seek to position 15.000
Input #0, matroska, from '1.mkv':
  Duration: 01:34:04.5, bitrate: N/A
  Stream #0.0: Video: h264, yuv420p, 1280x536, 23.98 fps(r)
  Stream #0.1: Audio: dca, 48000 Hz, 5:1
Unable for find a suitable output format for '2.mkv'

```

---

### Post by FakeOutdoorsman on 2010-02-19
It appears that FFmpeg from Hardy Medibuntu is too old to deal with this format.  I recommend compiling FFmpeg.  Visit the link above and follow the **C. Uninstalling FFmpeg and the Medibuntu Repository** section and then follow **A. Compiling FFmpeg yourself (for all Ubuntu versions)**.

---

### Post by AnotherNoob on 2010-02-20
after compling and installing the latest ffmpeg according to ur tut, this output comes up

```
FFmpeg version SVN-r21924, Copyright (c) 2000-2010 the FFmpeg developers
  built on Feb 21 2010 02:23:23 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 9. 0 / 50. 9. 0
  libavcodec    52.54. 0 / 52.54. 0
  libavformat   52.52. 0 / 52.52. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[matroska @ 0x8bab3a0]Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 48.00 (10000000/208333) -> 23.98 (24000/1001)
Input #0, matroska, from 'Daybreakers.2009.RC.LiNE.720p.BluRay.x264-RUBLU.mkv':
  Duration: 01:37:51.86, start: 0.000000, bitrate: 128 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 1280x544, PAR 1:1 DAR 40:17, 47.62 fps, 23.98 tbr, 1k tbn, 48 tbc
    Stream #0.1(eng): Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
Output #0, matroska, to '2.mkv':
  Metadata:
    encoder         : Lavf52.52.0
    Stream #0.0(eng): Video: libx264, yuv420p, 1280x544 [PAR 1:1 DAR 40:17], q=2-31, 1k tbn, 24 tbc
    Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 2 channels, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[matroska @ 0x8bbde00]st:0 error, pts < dts
av_interleaved_write_frame(): Error while opening file
```

---

### Post by dwpbike on 2010-07-21
> **FakeOutdoorsman said:**
> FFmpeg is still your best bet here.  What was the command that you used?  FFmpeg can be used to trim a video without re-encoding.  For example, I have a video that is 50 seconds in duration.  I want my output video to be 30 seconds long, but I want to skip the first 15 seconds of the input video.  I also don't want to re-encode anything so I'll just copy the video and audio streams.  My command would look like:
```
ffmpeg -ss 15 -t 30 -i input.mkv -acodec copy -vcodec copy output.mkv
```

after trying vlc record as the cutter (audio/video got out of sync), i found this advice to be my answer to extracting a flash video clip.  i did have to work with the "-t" option.  i found that "-t 1" gave me 42 sec of desired clip.  dividing the length of the clip by 42 gave me the required "-t" number.  i was able to get to the start of the clip on the source without clipping, so this may have affected the counter.

---

### Post by FakeOutdoorsman on 2010-07-21
I've experienced similar behavior as shown here:
[Frame rate being detected incorrectly in FLV](https://roundup.ffmpeg.org/issue1712)

FFmpeg SVN has fixed this issue, but you may be using an older FFmpeg revision.  You could compile FFmpeg and then *-t* would most likely work as expected:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

It would also be worth moving -ss and -t after the input, such as:
```
ffmpeg -i input.mkv -ss 15 -t 30 -acodec copy -vcodec copy output.mkv
```
...but I think using a more recent FFmpeg is your best bet.

---

### Post by jac_tict on 2011-03-26
> **FakeOutdoorsman said:**
> 
...
It would also be worth moving -ss and -t after the input
...

You are right!
Unbelievable!

---

### Post by d3v1150m471c on 2011-03-26
ffmpeg has a switch to keep the same quality from media to media:
```

ffmpeg -i input.avi -sameq output.avi

```

---

### Post by miteshbsjat on 2012-11-20
Hi,

You can try this perl script (using mencoder) to cut video files.
[http://miteshjlinuxtips.wordpress.com/2012/02/12/video-cutter-v2-video-cutting-using-mencoder/](http://miteshjlinuxtips.wordpress.com/2012/02/12/video-cutter-v2-video-cutting-using-mencoder/)

> **AnotherNoob said:**
> I m looking for a video cutter that cut a portion of video in the given format, i tried ffmpeg and avidemux but they touch( some modification) the original video so output doesn't remains same as the source 

is there any software for ubuntu 8.04 hardy which cuts the video portion as it is and have command line support 

Thanks for any help

Regards,
Mitesh

---

### Post by lisati on 2012-11-20
From the forum code of conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

