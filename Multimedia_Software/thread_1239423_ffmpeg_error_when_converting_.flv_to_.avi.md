---
title: "ffmpeg error when converting .flv to .avi"
date: 2009-08-13
forum: Multimedia Software
---

### Post by dopple on 2009-08-13
When using the following code
```
ffmpeg -i toxic.flv toxic.avi
```
I get the error
```
[flv @ 0xb80634c8]Unsupported video codec (7)
[flv @ 0xb80634c8]Could not find codec parameters (Video: 0x0007)
[flv @ 0xb80634c8]Could not find codec parameters (Audio: 0x000a, 44100 Hz, stereo)
```

The first line is repeated over 1024 times (More than my terminal scrollback allows.

Any ideas what's up?

---

### Post by FakeOutdoorsman on 2009-08-13
What version of Ubuntu are you using?  Show the complete FFmpeg output.

---

### Post by dopple on 2009-08-13
```
graham@graham-laptop:~/Desktop$ ffmpeg -i toxic.flv -ab 56 -ar 22050 -b 500 -s 320x240 video.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2

```
That's the beginning part then it's followed by...
```
[flv @ 0xb80634c8]Unsupported video codec (7)

```
... for a couple thousand lines, then

```
[flv @ 0xb80634c8]Could not find codec parameters (Video: 0x0007)
[flv @ 0xb80634c8]Could not find codec parameters (Audio: 0x000a, 44100 Hz, stereo)
```

---

### Post by dopple on 2009-08-13
Sorry I missed the version number. It's 8.10.
I found the following script flv2avi and it seems to do a bit more but still fails. Output is attatched minus tons of the lines that say "[flv @ 0x8720fe8]Unsupported video codec (7)"

```
graham@graham-laptop:~/Desktop$ ~/flv2avi toxic.flv
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x263f5a
libavformat file format detected.
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported audio codec (a)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Could not find codec parameters (Video: 0x0007)
[flv @ 0x8720fe8]Could not find codec parameters (Audio: 0x000a, 44100 Hz, stereo)
[flv @ 0x8720fe8]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 69, size 7609828, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 161, size 14702510, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 231, size 2892514, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 5, size 16601198, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 37, size 16650969, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 49, size 8149632, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 102, size 3728659, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 244, size 2743580, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 10, size 13736240, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 151, size 9598828, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 124, size 898103, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 186, size 14614740, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 108, size 2064372, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 12, size 6563868, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 26, size 1914548, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 21, size 5212288, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 125, size 3877615, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 100, size 7745555, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 163, size 13264613, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 174, size 5852410, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 1, size 3792900, flags 0
LAVF_header: av_find_stream_info() failed
libavformat file format detected.
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported audio codec (a)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Unsupported video codec (7)
[flv @ 0x8720fe8]Could not find codec parameters (Video: 0x0007)
[flv @ 0x8720fe8]Could not find codec parameters (Audio: 0x000a, 44100 Hz, stereo)
[flv @ 0x8720fe8]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 69, size 7609828, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 161, size 14702510, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 231, size 2892514, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 5, size 16601198, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 37, size 16650969, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 49, size 8149632, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 102, size 3728659, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 244, size 2743580, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 10, size 13736240, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 151, size 9598828, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 124, size 898103, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 186, size 14614740, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 108, size 2064372, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 12, size 6563868, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 26, size 1914548, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 21, size 5212288, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 125, size 3877615, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 100, size 7745555, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 163, size 13264613, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 174, size 5852410, flags 0
[flv @ 0x8720fe8]skipping flv packet: type 1, size 3792900, flags 0
LAVF_header: av_find_stream_info() failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
graham@graham-laptop:~/Desktop$ 

```

---

### Post by FakeOutdoorsman on 2009-08-13
You must be using Ubuntu Intrepid.  You need to enable restricted encoders.  Follow option "B" in this thread:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now you need to add a "k" after your bitrates in your FFmpeg command otherwise you'll encode at bits instead of kilobits:
```
ffmpeg -i toxic.flv -ab 56[color=#FF0000]k[/color] -ar 22050 -b 500[color=#FF0000]k[/color] -s 320x240 video.avi
```

---

### Post by dopple on 2009-08-13
When I tried option b I got 
```
graham@graham-laptop:~$ sudo apt-get install ffmpeg libavcodec-unstripped-51
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
libavcodec-unstripped-51 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The output for the command was
```
graham@graham-laptop:~/Desktop$ ffmpeg -i toxic.flv -ab 56k -ar 22050 -b 500k -s 320x240 video.avi
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[flv @ 0xb7fee4c8]Unsupported video codec (7)
[flv @ 0xb7fee4c8]Unsupported audio codec (a)
[flv @ 0xb7fee4c8]Unsupported video codec (7)
[flv @ 0xb7fee4c8]Unsupported video codec (7)
.
.
.
.
[flv @ 0xb7fee4c8]Unsupported video codec (7)
[flv @ 0xb7fee4c8]Unsupported video codec (7)
[flv @ 0xb7fee4c8]Could not find codec parameters (Video: 0x0007)
[flv @ 0xb7fee4c8]Could not find codec parameters (Audio: 0x000a, 44100 Hz, stereo)
toxic.flv: could not find codec parameters
graham@graham-laptop:~/Desktop$ 
```

---

### Post by FakeOutdoorsman on 2009-08-13
Post the complete output of (minus the hundreds of duplicate messages):
```
ffmpeg -i toxic.flv
```

It should look similar to:
```
$ ffmpeg -i toxic.flv 
FFmpeg version SVN-r19576, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-nonfree --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libx264 --enable-libtheora --enable-pthreads --enable-x11grab --arch=i686
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.37. 0 / 52.37. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Aug  3 2009 11:35:47, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'toxic.flv':
  Duration: 00:08:04.57, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: flv, yuv420p, 320x240, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, 1 channels, s16
At least one output file must be specified
```

---

### Post by dopple on 2009-08-14
It 's working. It must have been the way I downloaded the video (pulled from my /tmp/ dir.
I downloaded the same video from [http://keepvid.com](http://keepvid.com) and it's working now.
Thanks for your help FO!

---

### Post by FakeOutdoorsman on 2009-08-14
Good timing.  I was about to admit defeat.

---

