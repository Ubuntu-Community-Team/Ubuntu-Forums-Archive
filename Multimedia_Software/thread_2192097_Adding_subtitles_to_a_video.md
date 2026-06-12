---
title: "Adding subtitles to a video"
date: 2013-12-05
forum: Multimedia Software
---

### Post by alfirdaous on 2013-12-05
Hello everybody,

I've got a text file which has some words (subtitles), and I would like to merge it with a video using FFMPEG, is there any way to do so??

Thanks in advance

---

### Post by FakeOutdoorsman on 2013-12-06
What find of subtitles? What does ffmpeg say about your video and the subtitle file? Something like:

```
ffmpeg -i input.mp4 -i subtitles.srt
```

---

### Post by alfirdaous on 2013-12-06
This is the result:

```

ffmpeg version 0.8.9-6:0.8.9-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:15:53 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Q_hyCryvyuk.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2013-11-30 04:32:53
  Duration: 00:04:44.81, start: 0.000000, bitrate: 360 kb/s
    Stream #0.0(und): Video: h264 (Constrained Baseline), yuv420p, 480x360, 262 kb/s, 25 fps, 25 tbr, 50 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 96 kb/s
    Metadata:
      creation_time   : 2013-11-30 04:32:53
[srt @ 0x8d14ca0] Estimating duration from bitrate, this may be inaccurate
Input #1, srt, from 'Q_hyCryvyuk.srt':
  Duration: N/A, start: 32.956000, bitrate: N/A
    Stream #1.0: Subtitle: srt
At least one output file must be specified


```

---

### Post by shantiq on 2013-12-07
you can also use mencoder for this

```
mencoder -sub **file.srt**   -subfont-outline 4    -subcp iso-8857-9 -ovc x264 -oac copy   -o **filewithsub.mp4** **originalfile.mp4**
```

---

### Post by FakeOutdoorsman on 2013-12-08
Do you want to hardsub (burn in the subtitles; requires re-encoding) or use softsubs (any sane player will be able to choose the subtitle stream; no re-encoding required)?

---

### Post by alfirdaous on 2013-12-08
@[**[COLOR=#000000]shantiq[/COLOR]**]("http://ubuntuforums.org/member.php?u=870500"): This the result:
```

$ mencoder -sub Q_hyCryvyuk.srt -subfont-outline 4 -subcp iso-8857-9 -ovc x264 -oac copy -o Q_hyCryvyukBurned.mp4 Q_hyCryvyuk.mp4 
MEncoder svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
success: format: 0  data: 0x0 - 0xc3ee3d
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang und
VIDEO:  [H264]  480x360  24bpp  25.000 fps  262.2 kbps (32.0 kbyte/s)
[V] filefmt:44  fourcc:0x34363248  size:480x360  fps:25.000  ftime:=0.0400
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
SUB: error opening iconv descriptor.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio format 0x4134504d is incompatible with '-oac copy', please try '-oac pcm' instead or use '-fafmttag' to override it.

Exiting...


```

@[**[COLOR=#000000]FakeOutdoorsman[/COLOR]**]("http://ubuntuforums.org/member.php?u=162846"):

hardsub will burn them, if there are more than 1 subtitle we need to re-encode the video many times, how about softsubs, can we choose the subtitle that we need???

What is the command line for hardsub, I used:

```

ffmpeg -i Q_hyCryvyuk.mp4 -i Q_hyCryvyuk.srt -acodec copy -c:s mov_text -slang eng -vcodec libx264 -profile:v high -level:v 4.0 output.mp4

```

result:

```

Unrecognized option 'c:s'
Failed to set value 'mov_text' for option 'c:s'

```

---

### Post by FakeOutdoorsman on 2013-12-08
I see two issues here:

[list=1]
[*]Softsub support in mp4 is generally crappy. Using mkv would be a better choice, but if you need mp4 it can probably be used but some features (like italics, etc) from the srt file will be missing since you have to use mov_text (as far as I know).
[*]The "ffmpeg" in the repository is crappy. It is from a fork, not from FFmpeg, and this fake version is old, buggy, and lacks some subtitle features.
[/list]

**My examples here will not work with the fake so-called ffmpeg from the repository.** You'll have to get the real ffmpeg. You can:

[list]
[*]Simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds)
[*]Or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)
[/list]

[size=5]hardsubs[/size]

To burn-in hardsubs with ffmpeg see: [How to burn subtitles into the video](https://trac.ffmpeg.org/wiki/How%20to%20burn%20subtitles%20into%20the%20video). You'll have to use the real ffmpeg for this to work.

[size=5]softsubs[/size]

You'll have to use the real ffmpeg for this to work.

For softsubs you do not need to encode the video or the audio. Example for mp4:
```
ffmpeg -i movie.mkv -i englishsubs.srt -c:v copy -c:a copy -c:s mov_text -metadata:s:s:0 language=eng mov_text.mp4
```
Example for mkv:
```
ffmpeg -i movie.mkv -i englishsubs.srt -c copy -metadata:s:s:0 language=eng mov_text.mkv
```
Example for more languages:
```
ffmpeg -i movie.mkv -i englishsubs.srt -i frenchsubs.srt -map 0 -map 1 -map 2 -c copy -metadata:s:s:0 language=eng -metadata:s:s:1 language=fra subtitles.mkv
```
By default, ffmpeg includes only one stream of each type (video, audio, subtitle) present in the input files and adds them to each output file (see [stream selection](https://ffmpeg.org/ffmpeg.html#Stream-selection)). Since you now have two subtitles you have to explicitly tell ffmpeg to include all files from each input with [-map](http://ffmpeg.org/ffmpeg.html#Advanced-options).

---

### Post by alfirdaous on 2013-12-08
I used this command line, but still getting the same error:

```

$ ffmpeg -i Q_hyCryvyuk.mkv -i Q_hyCryvyuk.srt -vcodec copy -acodec copy -c:s mov_text -metadata:s:s:0 language=eng mov_text.mp4
ffmpeg version 0.8.9-6:0.8.9-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:15:53 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x82cb880] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'Q_hyCryvyuk.mkv':
  Metadata:
    MAJOR_BRAND     : mp42
    MINOR_VERSION   : 0
    COMPATIBLE_BRANDS: isommp42
    CREATION_TIME   : 2013-11-30 04:32:53
    ENCODER         : Lavf53.21.1
  Duration: 00:04:44.83, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0(und): Video: mpeg4 (Simple Profile), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 25 fps, 25 tbr, 1k tbn, 25 tbc (default)
    Stream #0.1(und): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s (default)
    Metadata:
      CREATION_TIME   : 2013-11-30 04:32:53
      LANGUAGE        : und
[srt @ 0x83012c0] Estimating duration from bitrate, this may be inaccurate
Input #1, srt, from 'Q_hyCryvyuk.srt':
  Duration: N/A, start: 32.956000, bitrate: N/A
    Stream #1.0: Subtitle: srt
Unrecognized option 'c:s'
Failed to set value 'mov_text' for option 'c:s'

```

---

### Post by shantiq on 2013-12-09
```
[COLOR=#000000][FONT=Ubuntu Mono]Audio format 0x4134504d is incompatible with '-oac copy', please try '-oac pcm' instead[/FONT][/COLOR]
``` mp4 sometimes needs this with mencoder


> [COLOR=#000000][FONT=Ubuntu Mono]mencoder -sub [/FONT][/COLOR]**file.srt**[COLOR=#000000][FONT=Ubuntu Mono]   -subfont-outline 4    -subcp iso-8857-9 -ovc x264 -oac [/FONT][/COLOR][COLOR=#800080][FONT=Ubuntu Mono]**pcm**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]   -o [/FONT][/COLOR]**filewithsub.mp4 ****originalfile.mp4**[COLOR=#000000][INDENT]

[/INDENT]
[/COLOR]


---

### Post by FakeOutdoorsman on 2013-12-09
> **alfirdaous said:**
> I used this command line, but still getting the same error:

My commands are for ffmpeg from FFmpeg.

---

### Post by alfirdaous on 2013-12-09
c:s means scodec, while trying it, it gives the bellow error:

```

$ ffmpeg -i Q_hyCryvyuk.mkv -i Q_hyCryvyuk.srt -vcodec copy -acodec copy -scodec mov_text -metadata:s:s:0 language=eng mov_text.mp4
ffmpeg version 0.8.9-6:0.8.9-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Nov  9 2013 19:15:53 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[matroska,webm @ 0x933a880] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from 'Q_hyCryvyuk.mkv':
  Metadata:
    MAJOR_BRAND     : mp42
    MINOR_VERSION   : 0
    COMPATIBLE_BRANDS: isommp42
    CREATION_TIME   : 2013-11-30 04:32:53
    ENCODER         : Lavf53.21.1
  Duration: 00:04:44.83, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0(und): Video: mpeg4 (Simple Profile), yuv420p, 480x360 [PAR 1:1 DAR 4:3], 25 fps, 25 tbr, 1k tbn, 25 tbc (default)
    Stream #0.1(und): Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s (default)
    Metadata:
      CREATION_TIME   : 2013-11-30 04:32:53
      LANGUAGE        : und
[srt @ 0x93702c0] Estimating duration from bitrate, this may be inaccurate
Input #1, srt, from 'Q_hyCryvyuk.srt':
  Duration: N/A, start: 32.956000, bitrate: N/A
    Stream #1.0: Subtitle: srt
[SIZE=4]**Unknown encoder 'mov_text'**[/SIZE]


```

---

### Post by alfirdaous on 2013-12-09
@[**[COLOR=#000000]shantiq[/COLOR]**]("http://ubuntuforums.org/member.php?u=870500"): The command works great, are there any params to change such as: font size, font face,...

Then, if the user download the video, are the subtitles will be in the video?

---

### Post by FakeOutdoorsman on 2013-12-10
> **alfirdaous said:**
> c:s means scodec, while trying it, it gives the bellow error:

As I mentioned before my commands will work for real ffmpeg from FFmpeg, but not the fake so-called "ffmpeg" in the repository. You will need to get the real ffmpeg. You can:

[list]
[*]Simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds)
[*]Or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)
[/list]

---

### Post by alfirdaous on 2013-12-10
Thx [**[COLOR=#000000]FakeOutdoorsman[/COLOR]**]("http://ubuntuforums.org/member.php?u=162846"), I will try it later on

---

