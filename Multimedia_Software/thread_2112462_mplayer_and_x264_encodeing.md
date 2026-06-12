---
title: "mplayer and x264 encodeing"
date: 2013-02-04
forum: Multimedia Software
---

### Post by Wolfpup on 2013-02-04
I found [x264 Encoding Guide - Linux Encoding]("https://sites.google.com/site/linuxencoding/x264-encoding-guide") after following the instructions there i ended up with the following bash script :

```

#!/bin/bash
vidfile='/home/wolfpup/Videos/<series folder>/<series ep>.mkv'
mplayer -nosound -benchmark -ass -vo yuv4mpeg:file=>(x264 --demuxer y4m --profile high --level 4.1 --crf 18 --preset veryslow --tune animation --deblock -2:-2 --psy-rd -0.60:0 --qpmin 10 --qpmax 28 --aq-mode 2 --no-mbtree --threads auto --output $vidfile.264 video.y4m 2>&1 | tee $vidfile-x264.log) $vidfile

```This script generates the following error :

```

x264 [error]: could not open input file `video.y4m'
MPlayer2 UNKNOWN (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/wolfpup/Videos/<series folder>/<series ep>.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/ASS), -sid 0, -slang und
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1280x720  24bpp  23.810 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in /home/wolfpup/Videos/<series folder>/
Using (default) progressive frame mode.
[ass] auto-open
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 [K V:   0.0   0/  0 ??% ??% ??,?% 0 0 [K V:   0.0   0/  0 ??% ??% ??,?% 0 0 [K 
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [yuv4mpeg] 1280x720 => 1280x720 Planar YV12 


MPlayer interrupted by signal 13 in module: check_framedrop
Colorspace details not fully supported by selected vo.


MPlayer interrupted by signal 13 in module: unknown

```Here is what I eventually want the script to fully do:

[LIST=1]
[*]encode the video adding hardsubs to video
[*]encode audio if needed(  eg flac/pcm -> aac) ( can be commented out if not needed).
[*]extract chapters file from mkv and audio if not encoded in previous step.
[*]mux new video, audio, and chapters file into and mp4 container.
[/LIST]

Right now I can not get the video to encode so I'm currently stuck.

ANY help will be GREATLY welcomed.

---

### Post by SeijiSensei on 2013-02-04
As its name implies, mplayer is a player, not an encoder. I don't know what you are reading, but mplayer is not designed to encode videos.

You might take a look at ffmpeg or avconv.

Also I'd recommend that you not include the names of infringing video files like the one you list here.  (Not to mention that HS is one of the worst examples of leeching in recent memory considering they don't even do their own translations but just steal them from Crunchyroll.)

---

### Post by Wolfpup on 2013-02-04
> **SeijiSensei said:**
> As its name implies, mplayer is a player, not an encoder. I don't know what you are reading, but mplayer is not designed to encode videos.

You might take a look at ffmpeg or avconv.

Also I'd recommend that you not include the names of infringing video files like the one you list here.  (Not to mention that HS is one of the worst examples of leeching in recent memory considering they don't even do their own translations but just steal them from Crunchyroll.)

I know mplayer is not an encoder that is what x264 is for please look as the FULL cmd line.
I am 'playing' the video+subs into x264 and x264 is doing the encoding.
 Also ffmpeg so not have the ability for allowing you to add the subs to the video stream unless you have a 'frame server' which is what I'm using mplayer for.

---

### Post by brainwash on 2013-02-04
> **Wolfpup said:**
> 
```

x264 [error]: could not open input file `video.y4m'
...

```

Are you sure that this non-existing file should be used as input source instead of the pipe from mplayer ( - )?

---

### Post by FakeOutdoorsman on 2013-02-04
> **Wolfpup said:**
> I found [x264 Encoding Guide - Linux Encoding]("https://sites.google.com/site/linuxencoding/x264-encoding-guide")

Old. You no longer need to use mplayer to pipe to x264; it can handle any input that ffmpeg supports. You need to enable lavf support in x264 (basically you install x264 then ffmpeg then x264 again if you want both ffmpeg to support libx264 and x264 to support lavf). Search lavf in [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

Or you could just use ffmpeg.

[QUOTE=Wolfpup]Here is what I eventually want the script to fully do:[LIST=1]
[*]encode the video adding hardsubs to video
[*]encode audio if needed(  eg flac/pcm -> aac) ( can be commented out if not needed).
[*]extract chapters file from mkv and audio if not encoded in previous step.
[*]mux new video, audio, and chapters file into and mp4 container.
[/LIST][/quote]

A good start:
```
ffmpeg -i input -c:v libx264 -preset veryslow -tune animation -crf 18 \
-vf subtitles=subtitle.srt -c:a libfdk_aac -vbr 5 output.mkv
```

You will have to figure out how to extract the srt and how to deal with chapters. The bizarro "ffmpeg" from the repo does not have the subtitles filter so you will need to compile as shown in the link I provided above.

Also see:
[list]
[*][FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)
[*][FFmpeg and AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide)
[*][How to burn subtitles into the video with ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video)
[/list]

---

### Post by Wolfpup on 2013-02-05
> **FakeOutdoorsman said:**
> Old. You no longer need to use mplayer to pipe to x264; it can handle any input that ffmpeg supports. You need to enable lavf support in x264 (basically you install x264 then ffmpeg then x264 again if you want both ffmpeg to support libx264 and x264 to support lavf). Search lavf in [How To Compile FFmpeg and x264 on Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").

Or you could just use ffmpeg.



A good start:
```
ffmpeg -i input -c:v libx264 -preset veryslow -tune animation -crf 18 \
-vf subtitles=subtitle.srt -c:a libfdk_aac -vbr 5 output.mkv
```You will have to figure out how to extract the srt and how to deal with chapters. The bizarro "ffmpeg" from the repo does not have the subtitles filter so you will need to compile as shown in the link I provided above.

Also see:
[LIST]
[*][FFmpeg and x264 Encoding Guide]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide")
[*][FFmpeg and AAC Encoding Guide]("https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide")
[*][How to burn subtitles into the video with ffmpeg]("https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video")
[/LIST]


After following the above instructions i do have it semi encoding the mp4.
I had to convert :
```

mplayer -nosound -benchmark -ass -vo yuv4mpeg:file=>(x264 --demuxer y4m --profile high --level 4.1 --crf 18 --preset veryslow --tune animation --deblock -2:-2 --psy-rd -0.60:0 --qpmin 10 --qpmax 28 --aq-mode 2 --no-mbtree --threads auto --output $vidfile.264 video.y4m 2>&1 | tee $vidfile-x264.log) $vidfile

```
To: 
```

ffmpeg -i $vidfile.mkv -c:v libx264 -profile:v high -level 4.1 -crf 18 -preset veryslow -tune animation -deblock -2:-2 -x264opts qpmin=10:qpmax=28:aq-mode=2:no-mbtree:threads=auto -c:a copy $vidfile.mp4 2>&1 | tee $vidfile-enc.log

```
 this dose do the video re-encoeing BUT it dose not include the subs wich are embeded in the mkv container. So next step is to figure out how to extrat the fonts and install them plus extract the subs which are advanced subtitle scripting. i wouls like to be able to do this all automatically so that i can put the script in a bin folder and then just use a simple command to do all the processing for a given video file.

---

### Post by evilsoup on 2013-02-05
To extract subtitles:

```

ffmpeg -i input.mkv -map 0:s:0 subtitle.srt

```

This will extract the first subtitle stream (ffmpeg begins counting at 0). If you have multiple subtitle languages & want to extract the second stream, use `-map 0:s:1`.

If you have Advanced Substation Alpha subtitles, you should use `subtitle.ass` as the output.

The instructions on how to hardcode the subtitles, once they are in a separate file, are clearly laid out in that guide fakeoutdoorsman linked to.

---

### Post by Wolfpup on 2013-02-05
> **evilsoup said:**
> To extract subtitles:

```

ffmpeg -i input.mkv -map 0:s:0 subtitle.srt

```This will extract the first subtitle stream (ffmpeg begins counting at 0). If you have multiple subtitle languages & want to extract the second stream, use `-map 0:s:1`.

If you have Advanced Substation Alpha subtitles, you should use `subtitle.ass` as the output.

The instructions on how to hardcode the subtitles, once they are in a separate file, are clearly laid out in that guide fakeoutdoorsman linked to.
i want the subs to be burned into the video preferably with out having to extract them plus there are fonts in the file that are included in the mkv. and there is also the chapters that would need to be added to the mp4 from the mkv.

---

### Post by FakeOutdoorsman on 2013-02-07
Why no-mbtree?

---

