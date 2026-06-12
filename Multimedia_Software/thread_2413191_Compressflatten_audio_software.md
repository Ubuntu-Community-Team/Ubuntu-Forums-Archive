---
title: "Compress/flatten audio software"
date: 2019-02-22
forum: Multimedia Software
---

### Post by bandito40 on 2019-02-22
Looking for software recommendations to compress/flatten the audio of a video that I have. Doesn't have to do it automatically.

Thanks

---

### Post by bitsnpcs on 2019-02-22
Hello,

if you separate the audio file you can do this in **Audacity**, it is available in Ubuntu Software.

You can separate the audio from a video using **VLC Media player**, also available in Ubuntu Software, you make a custom template and save the audio only, then put this in to Audacity.

I am not sure if you can separate the audio in **Openshot**, but you can use it to join audio in to a video as I have done this before.

---

### Post by bandito40 on 2019-02-22
I thought of that but because the audio is dialogue I didn't want to have the dialogue not match the movement of the mouths when adding it back. I may end up just doing it that way though.

---

### Post by bitsnpcs on 2019-02-22
It can go out of sync if you reduce the length of the audio, but if you cut each piece of dialogue in to a file and align this using a timeline for the video.
It would need some natural sounding background noise between the speech on low volume to make it natural, or you can use titles and/or video transitions between each part of the dialogue, then you don't need to add additional sound, like they are individual scenes.

It can make the editing a longer process but you have full control and accuracy over it, when compared to an automated method.

---

### Post by shantiq on 2019-02-28
***[COLOR=#000000]bandito40[/COLOR]*** 

you can use ffmpeg from command line this way:


If you have only one audio stream in your video it is ***very easy*** >>


```
 ffmpeg -i input.avi -c:v copy   -b:a 64k  output.avi
```
[I]

-c:v copy   copies your video stream same as original
-b:a 64k    lowers your audio bitrate to 64k and defaults to mp3 as a codec[/I]

* if you add -c:a ac3 you keep it as  ac3 instead of default mp3*

```
 ffmpeg -i input.avi -c:v copy   -c:a ac3 -b:a 64k  output.avi
```


=========================



*** NOW   if your video has more than one audio stream it is a tad more difficult***

&#10122; run

```
ffmpeg -i input.avi
```    to see what is in there


example:

```
ffmpeg -i "Modesty Blaise".avi
ffmpeg version N-91586-g90dc584 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-openssl --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 18.102 / 56. 18.102
  libavcodec     58. 22.101 / 58. 22.101
  libavformat    58. 17.101 / 58. 17.101
  libavdevice    58.  4.101 / 58.  4.101
  libavfilter     7. 26.100 /  7. 26.100
  libswscale      5.  2.100 /  5.  2.100
  libswresample   3.  2.100 /  3.  2.100
  libpostproc    55.  2.100 / 55.  2.100
Input #0, avi, from 'Modesty Blaise.avi':
  Metadata:
    encoder         : FairUse Wizard - http://fairusewizard.com
  Duration: 01:59:40.84, start: 0.000000, bitrate: 1749 kb/s
*[COLOR=#006400]    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 704x368 [SAR 1:1 DAR 44:23], 1350 kb/s, 23.98 fps, 23.98 tbr, 23.98 tbn, 23.98 tbc[/COLOR]*
 [I][COLOR=#800000]   Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s
    Stream #0:2: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s[/COLOR][/I]
At least one output file must be specified


```

you can see there are 2 AUDIO streams here


&#10123; so to pick the second stream you need to do this >>


```
ffmpeg -i "Modesty Blaise".avi -map 0:0 -b:v 1350k -map 0:2 -c:a ac3 -b:a 64k  Modesty64k.avi
```

-map 0:0   copy the green video stream *YOU NEED*  to add -b:v 1350k to retain original video bitrate 
      -map 0:2   copies the SECOND audio stream -c:a ac3 -b:a 64k makes the codec remain ac3 and lowers bitrate to 64k


* you will get this [check output in red]>>*

```
ffmpeg -i "Modesty Blaise".avi -map 0:0 -b:v 1350k  -map 0:2 -c:a ac3 -b:a 64k     Modesty64k.avi
ffmpeg version N-91586-g90dc584 Copyright (c) 2000-2018 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
  configuration: --prefix=/home/shan/ffmpeg_build --pkg-config-flags=--static --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --extra-libs='-lpthread -lm' --bindir=/home/shan/bin --enable-gpl --enable-libaom --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-openssl --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libx265 --enable-nonfree
  libavutil      56. 18.102 / 56. 18.102
  libavcodec     58. 22.101 / 58. 22.101
  libavformat    58. 17.101 / 58. 17.101
  libavdevice    58.  4.101 / 58.  4.101
  libavfilter     7. 26.100 /  7. 26.100
  libswscale      5.  2.100 /  5.  2.100
  libswresample   3.  2.100 /  3.  2.100
  libpostproc    55.  2.100 / 55.  2.100
Input #0, avi, from 'Modesty Blaise.avi':
  Metadata:
    encoder         : FairUse Wizard - http://fairusewizard.com
  Duration: 01:59:40.84, start: 0.000000, bitrate: 1749 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 704x368 [SAR 1:1 DAR 44:23], 1350 kb/s, 23.98 fps, 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s
    Stream #0:2: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 192 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 (native) -> mpeg4 (native))
  Stream #0:2 -> #0:1 (ac3 (native) -> ac3 (native))
Press [q] to stop, [?] for help
[mpeg4 @ 0x5611e6cb85c0] Video uses a non-standard and wasteful way to store B-frames ('packed B-frames'). Consider using the mpeg4_unpack_bframes bitstream filter without encoding but stream copy to fix it.
[I][COLOR=#800000]Output #0, avi, to 'Modesty64k.avi':
  Metadata:
    ISFT            : Lavf58.17.101
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 704x368 [SAR 1:1 DAR 44:23], q=2-31, 1350 kb/s, 23.98 fps, 23.98 tbn, 23.98 tbc
    Metadata:
      encoder         : Lavc58.22.101 mpeg4
    Side data:
      cpb: bitrate max/min/avg: 0/0/1350000 buffer size: 0 vbv_delay: -1
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, stereo, fltp, 64 kb/s[/COLOR][/I]
    Metadata:
      encoder         : Lavc58.22.101 ac3
frame=90518 fps=822 q=3.7 Lsize=  656706kB time=01:02:56.00 bitrate=1424.7kbits/s speed=34.3x   

```


and obtain this video read here in [mpv]("https://mpv.io/installation/") [shift+i]   to see metadata   [mpv is a truly excellent player]

[[IMG]https://i.postimg.cc/V5bBgkDL/ff.png[/IMG]]("https://postimg.cc/V5bBgkDL")

---

