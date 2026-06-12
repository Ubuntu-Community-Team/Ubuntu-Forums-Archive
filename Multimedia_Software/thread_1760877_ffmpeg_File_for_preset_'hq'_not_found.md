---
title: "ffmpeg: File for preset 'hq' not found"
date: 2011-05-17
forum: Multimedia Software
---

### Post by spark3y on 2011-05-17
Why do i get the following message when trying to convert in ffmpeg?

File for preset 'hq' not found

---

### Post by andrew.46 on 2011-05-18
> **spark3y said:**
> Why do i get the following message when trying to convert in ffmpeg?

```
File for preset 'hq' not found
```

There have been many changes with the FFmpeg presets so it really depends on which version you are running. An easy way to find what presets you have installed is to run the following command:

```

$ **[COLOR="Red"]sudo find /usr -iname '*.ffpreset'[/COLOR]**
/usr/share/ffmpeg/libvpx-720p50_60.ffpreset
/usr/share/ffmpeg/libx264-lossless_slow.ffpreset
/usr/share/ffmpeg/libvpx-720p.ffpreset
/usr/share/ffmpeg/libvpx-1080p.ffpreset
/usr/share/ffmpeg/libvpx-1080p50_60.ffpreset
/usr/share/ffmpeg/libx264-baseline.ffpreset
/usr/share/ffmpeg/libx264-lossless_slower.ffpreset
/usr/share/ffmpeg/libvpx-360p.ffpreset
/usr/share/ffmpeg/libx264-lossless_fast.ffpreset
/usr/share/ffmpeg/libx264-lossless_max.ffpreset
/usr/share/ffmpeg/libx264-lossless_ultrafast.ffpreset
/usr/share/ffmpeg/libx264-ipod320.ffpreset
/usr/share/ffmpeg/libx264-ipod640.ffpreset
/usr/share/ffmpeg/libx264-lossless_medium.ffpreset

```

Mind you if you are running the git FFmpeg (as I am) presets have changed again as x264 presets are called with the *-preset* option. But I suspect the above 'find' command should help you out... If not could you post the full commandline you are using and the terminal output?

---

### Post by spark3y on 2011-05-18
Thank you for your answer!

The output shows the following.

```

user@Server:~$ sudo find /usr -iname '*.ffpreset'
/usr/local/share/ffmpeg/libx264-lossless_medium.ffpreset
/usr/local/share/ffmpeg/libx264-lossless_slow.ffpreset
/usr/local/share/ffmpeg/libx264-lossless_fast.ffpreset
/usr/local/share/ffmpeg/libx264-lossless_ultrafast.ffpreset
/usr/local/share/ffmpeg/libx264-lossless_slower.ffpreset
/usr/local/share/ffmpeg/libx264-ipod640.ffpreset
/usr/local/share/ffmpeg/libx264-baseline.ffpreset
/usr/local/share/ffmpeg/libx264-ipod320.ffpreset
/usr/local/share/ffmpeg/libx264-lossless_max.ffpreset

```

Okay so the -vpre switch has been replaced with -preset ?

---

### Post by andrew.46 on 2011-05-18
> **spark3y said:**
> Okay so the -vpre switch has been replaced with -preset ?

Well that depends on what version of FFmpeg you have :). You can still use the presets that you have in /usr/local/share/ with *-vpre*, but if you have the current git FFmpeg, as I demonstrate here:

```

andrew@skamandros~$[B][COLOR="Red"] ffmpeg -h | grep 'preset'
ffmpeg version git-N-29991-g34b92db, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 17 2011 18:35:57 with gcc 4.5.2[/COLOR][/B]
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc --enable-avfilter --enable-pthreads --enable-shared --disable-static --disable-ffserver --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libvpx --enable-zlib --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libvo-amrwbenc --enable-libvo-aacenc --enable-libfreetype --enable-nonfree --enable-gpl --enable-version3
  libavutil    51.  2. 1 / 51.  2. 1
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  1. 0 / 53.  1. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  5. 0 /  2.  5. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
-fpre filename      set options from indicated preset file
-vpre preset        set the video options to the indicated preset
-apre preset        set the audio options to the indicated preset
-spre preset        set the subtitle options to the indicated preset
**[COLOR="Red"]-preset            <string> E.V.. Set the encoding preset[/COLOR]**

```

you can also use presets drawn directly from x264 with the *-preset *option, at the moment these are ultrafast, superfast, veryfast, faster, fast, medium, slow, slower, veryslow and placebo.

---

### Post by spark3y on 2011-05-19
Thanks again for your answer.

I got the following from looking up the version
```

ffmpeg version git-N-29958-g68bed67, Copyright (c) 2000-2011 the FFmpeg developers
  built on May 16 2011 18:54:08 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51.  2. 1 / 51.  2. 1
  libavcodec   53.  5. 0 / 53.  5. 0
  libavformat  53.  1. 0 / 53.  1. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  5. 0 /  2.  5. 0
  libswscale    0. 14. 0 /  0. 14. 0
  libpostproc  51.  2. 0 / 51.  2. 0
ffmpeg git-N-29958-g68bed67
libavutil    51.  2. 1 / 51.  2. 1
libavcodec   53.  5. 0 / 53.  5. 0
libavformat  53.  1. 0 / 53.  1. 0
libavdevice  53.  0. 0 / 53.  0. 0
libavfilter   2.  5. 0 /  2.  5. 0
libswscale    0. 14. 0 /  0. 14. 0
libpostproc  51.  2. 0 / 51.  2. 0

```

How can i get the hq preset to work? Sry if i am sounding stupid :)

---

### Post by andrew.46 on 2011-05-19
> **spark3y said:**
> How can i get the hq preset to work? Sry if i am sounding stupid :)

You are not sounding stupid at all :). Try something like the following for the x264 part of your commandline:

```
-vcodec libx264 -preset slow -crf 22
```

and I believe this should give you a result that will be at least equal quality to the old hq preset.

---

### Post by spark3y on 2011-05-19
Thanks a bunch m8 :)

---

### Post by kisugira on 2011-09-25
i cant use presets. (hq + others)

watch this :
ffmpeg -v 9 -loglevel 99 -f x11grab -qscale 2 -r 15 -s 1680x970 -i :0.0+0,51 -s 1680x970 -vcodec libx264 -preset lossless_fast -crf 24 -threads 0 grab.mp4

ffmpeg version N-32226-ga9c6936, Copyright (c) 2000-2011 the FFmpeg developers
  built on Aug 31 2011 18:30:28 with gcc 4.4.3
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil    51. 14. 0 / 51. 14. 0
  libavcodec   53. 12. 0 / 53. 12. 0
  libavformat  53. 10. 0 / 53. 10. 0
  libavdevice  53.  3. 0 / 53.  3. 0
  libavfilter   2. 37. 0 /  2. 37. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[x11grab @ 0x187a420] device: :0.0+0,51 -> display: :0.0 x: 0 y: 51 width: 1680 height: 970
[x11grab @ 0x187a420] shared memory extension found
[x11grab @ 0x187a420] All info found
[x11grab @ 0x187a420] Estimating duration from bitrate, this may be inaccurate
Input #0, x11grab, from ':0.0+0,51':
  Duration: N/A, start: 1316946162.088944, bitrate: 782208 kb/s
    Stream #0.0, 1, 1/1000000: Video: rawvideo (BGRA / 0x41524742), bgra, 1680x970, 1/15, 782208 kb/s, 15 tbr, 1000k tbn, 15 tbc
File 'grab.mp4' already exists. Overwrite ? [y/N] y
Incompatible pixel format 'bgra' for codec 'libx264', auto-selecting format 'yuv420p'
[buffer @ 0x18888a0] w:1680 h:970 pixfmt:bgra tb:1/1000000 sar:0/1 sws_param:
[buffersink @ 0x1876c40] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x18773e0] w:1680 h:970 fmt:bgra -> w:1680 h:970 fmt:yuv420p flags:0x4
x264 [error]: invalid preset 'lossless_fast'
[libx264 @ 0x1874220] Error setting preset/tune lossless_fast/(null).
Output #0, mp4, to 'grab.mp4':
    Stream #0.0, 0, 1/90000: Video: h264, yuv420p, 1680x970, 1/15, q=2-31, 90k tbn, 15 tbc
Stream mapping:
  Stream #0.0 -> #0.0 (rawvideo -> libx264)
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height


but i have the presets in my home:
ls -la ~/.ffmpeg/
total 80
drwxr-xr-x  2 user user  4096 2011-09-25 11:43 .
drwxr-xr-x 96 user user 12288 2011-09-25 11:43 ..
-rw-r--r--  1 user user    50 2011-09-25 11:43 libx264-baseline.ffpreset
-rw-r--r--  1 user user   304 2011-09-25 11:43 libx264-default.ffpreset
-rw-r--r--  1 user user   322 2011-09-25 11:43 libx264-fastfirstpass.ffpreset
-rw-r--r--  1 user user   304 2011-09-25 11:43 libx264-hq.ffpreset
-rw-r--r--  1 user user    90 2011-09-25 11:43 libx264-ipod320.ffpreset
-rw-r--r--  1 user user   100 2011-09-25 11:43 libx264-ipod640.ffpreset
-rw-r--r--  1 user user   273 2011-09-25 11:43 libx264-lossless_fast.ffpreset
-rw-r--r--  1 user user   299 2011-09-25 11:43 libx264-lossless_max.ffpreset
-rw-r--r--  1 user user   273 2011-09-25 11:43 libx264-lossless_medium.ffpreset
-rw-r--r--  1 user user   298 2011-09-25 11:43 libx264-lossless_slower.ffpreset
-rw-r--r--  1 user user   287 2011-09-25 11:43 libx264-lossless_slow.ffpreset
-rw-r--r--  1 user user   264 2011-09-25 11:43 libx264-lossless_ultrafast.ffpreset
-rw-r--r--  1 user user    22 2011-09-25 11:43 libx264-main.ffpreset
-rw-r--r--  1 user user   316 2011-09-25 11:43 libx264-max.ffpreset
-rw-r--r--  1 user user   293 2011-09-25 11:43 libx264-normal.ffpreset
-rw-r--r--  1 user user   293 2011-09-25 11:43 libx264-slowfirstpass.ffpreset

---

### Post by onizukal on 2012-02-26
Hey Dudes!! 

It is little bit old topics but when i was googling i found that answer so maybe you can help me . 

when i make a query for currently preset values in my system , the reply is : 


hamza@hamza-PC:~$ sudo find /usr -iname '*.ffpreset'
[sudo] password for hamza: 
/usr/local/share/ffmpeg/libvpx-720p.ffpreset
/usr/local/share/ffmpeg/libvpx-360p.ffpreset
/usr/local/share/ffmpeg/libvpx-720p50_60.ffpreset
/usr/local/share/ffmpeg/libvpx-1080p50_60.ffpreset
/usr/local/share/ffmpeg/libx264-ipod640.ffpreset
/usr/local/share/ffmpeg/libx264-ipod320.ffpreset
/usr/local/share/ffmpeg/libvpx-1080p.ffpreset

but i need to use some -vpre or preset values like medium or fast. When i use ffmpeg , output is saying like i didnt have them . So how can i obtain such as those preset values ?  

ffmpeg output errors : 

[libx264 @ 0xad22880] broken ffmpeg default settings detected
[libx264 @ 0xad22880] use an encoding preset (e.g. -vpre medium)
[libx264 @ 0xad22880] preset usage: -vpre <speed> -vpre <profile>
[libx264 @ 0xad22880] speed presets are listed in x264 --help
[libx264 @ 0xad22880] profile is optional; x264 defaults to high

Thank you in advance

---

### Post by OrcLex on 2012-03-01
same here:

$ ll /usr/local/share/ffmpeg/
insgesamt 48K
drwxr-xr-x  2 root root 4,0K 2012-03-01 10:46 .
drwxr-xr-x 10 root root 4,0K 2012-03-01 10:45 ..
-rw-r--r--  1 root root 8,7K 2012-03-01 10:45 ffprobe.xsd
-rw-r--r--  1 root root  212 2012-03-01 10:45 libvpx-1080p50_60.ffpreset
-rw-r--r--  1 root root  212 2012-03-01 10:45 libvpx-1080p.ffpreset
-rw-r--r--  1 root root  204 2012-03-01 10:45 libvpx-360p.ffpreset
-rw-r--r--  1 root root  212 2012-03-01 10:45 libvpx-720p50_60.ffpreset
-rw-r--r--  1 root root  212 2012-03-01 10:45 libvpx-720p.ffpreset
-rw-r--r--  1 root root   58 2012-03-01 10:45 libx264-ipod320.ffpreset
-rw-r--r--  1 root root   61 2012-03-01 10:45 libx264-ipod640.ffpreset

Using an old preset from an old configuration doesn't work anymore:
.ffmpeg/libx264-veryslow_firstpass.ffpreset: Invalid option or argument: 'rc_lookahead=60', parsed as 'rc_lookahead' = '60'

Where can I get new ffpresets for libx264 with very high quality?

---

### Post by OrcLex on 2012-03-01
to reply my own question:

the old ffpresets are removed due to replacement:
[http://git.videolan.org/?p=ffmpeg.git;a=commitdiff;h=1279098d7bea4440036fb50884773d620b00812c](http://git.videolan.org/?p=ffmpeg.git;a=commitdiff;h=1279098d7bea4440036fb50884773d620b00812c)

Now you can pass the x264 preset parameter to ffmpeg:

--preset <string>       Use a preset to select encoding settings [medium]
    Overridden by user settings.
    - ultrafast:
      --no-8x8dct --aq-mode 0 --b-adapt 0 
      --bframes 0 --no-cabac --no-deblock 
      --no-mbtree --me dia --no-mixed-refs
      --partitions none --rc-lookahead 0 --ref 1
      --scenecut 0 --subme 0 --trellis 0 
      --no-weightb --weightp 0
    - superfast:
      --no-mbtree --me dia --no-mixed-refs
      --partitions i8x8,i4x4 --rc-lookahead 0
      --ref 1 --subme 1 --trellis 0 --weightp 1 
    - veryfast:
      --no-mixed-refs --rc-lookahead 10
      --ref 1 --subme 2 --trellis 0 --weightp 1 
    - faster:
      --no-mixed-refs --rc-lookahead 20
      --ref 2 --subme 4 --weightp 1 
    - fast:
      --rc-lookahead 30 --ref 2 --subme 6
      --weightp 1
    - medium:
      Default settings apply. 
    - slow:
      --b-adapt 2 --direct auto --me umh
      --rc-lookahead 50 --ref 5 --subme 8
    - slower:
      --b-adapt 2 --direct auto --me umh
      --partitions all --rc-lookahead 60
      --ref 8 --subme 9 --trellis 2 
    - veryslow:
      --b-adapt 2 --bframes 8 --direct auto
      --me umh --merange 24 --partitions all
      --ref 16 --subme 10 --trellis 2
      --rc-lookahead 60
    - placebo:
      --bframes 16 --b-adapt 2 --direct auto
      --slow-firstpass --no-fast-pskip
      --me tesa --merange 24 --partitions all
      --rc-lookahead 60 --ref 16 --subme 11
      --trellis 2

---

