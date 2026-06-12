---
title: "avconv MKV-&gt;MP4 &quot;pts &lt; dts in stream 0&quot; error"
date: 2013-03-20
forum: Multimedia Software
---

### Post by gravey on 2013-03-20
Hello -

I'm trying to remux an MKV file to MP4 using the following command:

```
avconv -i file.mkv -c:v copy -c:a copy file.mp4
```

avconv fails with the following output:

```

[COLOR=#ff8c00][matroska,webm @ 0x133ef60] max_analyze_duration reached[/COLOR]
[COLOR=#ff8c00][matroska,webm @ 0x133ef60] Estimating duration from bitrate, this may be inaccurate[/COLOR]
Input #0, matroska,webm, from 'file.mkv':
  Duration: 00:42:33.66, start: 0.000000, bitrate: 384 kb/s
    Stream #0.0(eng): Video: h264 (High), yuv420p, 1280x718 [PAR 1:1 DAR 640:359], 23.98 fps, 23.98 tbr, 1k tbn, 2k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s (default)
    Stream #0.2: Subtitle: [0][0][0][0] / 0x0000 (default)
Output #0, mp4, to 'The Americans S01E07.mp4':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0(eng): Video: ![0][0][0] / 0x0021, yuv420p, 1280x718 [PAR 1:1 DAR 640:359], q=2-31, 1k tbn, 1k tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, 384 kb/s (default)
Stream mapping:
  Stream #0:0 -> #0:0 (copy)
  Stream #0:1 -> #0:1 (copy)
Press ctrl-c to stop encoding
[COLOR=#ff0000]**[mp4 @ 0x1479120] pts < dts in stream 0**[/COLOR]
[COLOR=#ff0000]**av_interleaved_write_frame(): Invalid argument**[/COLOR]

```

Any suggestions on how to fix this error?

Thanks in advance for any help.


mediainfo output is as follows:
```
GeneralUnique ID                                : 249517535331217033373395087239106118949 (0xBBB7544CA36DD4ADA32E867FF689C525)
Complete name                            : file.mkv
Format                                   : Matroska
Format version                           : Version 4 / Version 2
File size                                : 1.35 GiB
Duration                                 : 42mn 33s
Overall bit rate                         : 4 543 Kbps
Encoded date                             : UTC 2013-03-15 04:07:30
Writing application                      : mkvmerge v6.1.0 ('Old Devil') built on Mar  2 2013 14:32:37
Writing library                          : libebml v1.3.0 + libmatroska v1.4.0


Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 2 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 42mn 33s
Bit rate                                 : 4 069 Kbps
Width                                    : 1 280 pixels
Height                                   : 718 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.185
Stream size                              : 1.21 GiB (90%)
Language                                 : English
Default                                  : Yes
Forced                                   : No
Color primaries                          : BT.709
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.709


Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Codec ID                                 : A_AC3
Duration                                 : 42mn 33s
Bit rate mode                            : Constant
Bit rate                                 : 384 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 117 MiB (8%)
Language                                 : English
Default                                  : Yes
Forced                                   : No


Text
ID                                       : 3
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Default                                  : Yes
Forced                                   : No

```

---

### Post by gravey on 2013-03-27
Bump

---

### Post by gravey on 2013-03-27
.

---

### Post by andrew.46 on 2013-03-28
Have you updated your copy of avconv to the latest git?

---

### Post by gravey on 2013-03-28
Appears I'm up to date, as there are no upgrades available via apt. 

avconv -version gives me:
```
0.8.5-6:0.8.5-0ubuntu0.12.10.1
```

I do see there's a version 9 available on git. What's the best way to go about upgrading since apt is showing that I'm up to date?

---

### Post by andrew.46 on 2013-03-28
I have to admit that I don't follow avconv I use FFmpeg. This can be updated easily enough:

[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

and this might be the best way to get a more recent copy that with any luck will not have the bug in your existing copy.

---

### Post by gravey on 2013-03-28
Thanks for the pointer. I went ahead and updated avconv to version 9.4, built from git. 

Using the same command and file as in my original post, I'm now getting a similar but slightly more descriptive error:
```
[mp4 @ 0x20b2020] Application provided invalid, non monotonically increasing dts to muxer in stream 0: 83 >= 42
av_interleaved_write_frame(): Invalid argument
```

---

### Post by andrew.46 on 2013-03-28
Hmmm... this may be fixed in FFmpeg:

[http://ffmpeg.org/trac/ffmpeg/ticket/1154](http://ffmpeg.org/trac/ffmpeg/ticket/1154)

---

### Post by gravey on 2013-04-01
Andrew - good call.  I compiled FFmpeg from git with the instructions above, and the problem appears to be fixed.  Guess I'll be sticking with FFmpeg over avconv.

Appreciate the help!

---

### Post by andrew.46 on 2013-04-02
Great news :)

---

### Post by FakeOutdoorsman on 2013-04-02
I prefer to compile, but for the lazy, or for those who need to keep the system so-called "ffmpeg" package for dependent programs, the static builds are an easy alternative ([instructions](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453)).

---

