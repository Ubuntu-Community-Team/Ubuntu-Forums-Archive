---
title: "How i add subtitle in ffmpeg"
date: 2011-07-17
forum: Multimedia Software
---

### Post by Lord.vegeta on 2011-07-17
Hi i have a mp4 file and i will convert it with ffmpeg and add new subtitle i use this command

```
ffmpeg -i Taylor-Swift-Mine.mp4 -b 768000 -r 24 -s 640x360 -aspect 16:9 -newsubtitle Mine.srt -ab 128000 -ac 2 -ar 44100 out.mp4
```and output command

```
ffmpeg version N-30884-g54dd50d, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 20 2011 19:09:46 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    0. 14. 1 /  0. 14. 1
  libpostproc  51.  2. 0 / 51.  2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Taylor-Swift-Mine.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    creation_time   : 2011-07-06 06:37:12
    encoder         : HandBrake 0.9.5 2011010300
  Duration: 00:03:55.06, start: 0.000000, bitrate: 1519 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1920x1072, 1360 kb/s, 23.98 fps, 23.98 tbr, 90k tbn, 47.95 tbc
    Metadata:
      creation_time   : 2011-07-06 06:37:13
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 154 kb/s
    Metadata:
      creation_time   : 2011-07-06 06:37:13
At least one output file must be specified

```Do you see i can't convert my file now how i add subtitle to my video in ffmpeg

---

### Post by FakeOutdoorsman on 2011-07-17
[FFmpeg documentation](http://ffmpeg.org/ffmpeg-doc.html) says:
> The -newvideo, -newaudio and -newsubtitle options have to be specified immediately after the name of the output file to which you want to add them.
Example:
```
ffmpeg -i Taylor-Swift-Mine.mp4 -i Mine.srt -vcodec libx264 -preset medium -crf 24 -slang foo \
-vf scale="640:trunc(ow/a/2)*2" -threads 0 -acodec copy -scodec copy output.mkv -newsubtitle
```
I made some changes to your command:
[list]
[*]Make output video H.264 instead of MPEG-4 Part 2.
[*]Copy audio instead of re-encoding.
[*]Scale to 640 width and have FFmpeg automatically determine proper height to keep aspect.
[*]Use MKV as output container (I'm not sure if MP4 works with subtitles very well).
[*]Add *-slang foo* to set the language code of the subtitle stream (this is optional). See [List of ISO 639-2 codes](http://en.wikipedia.org/wiki/List_of_ISO_639-2_codes) for your desired three letter language code.
[/list]

---

