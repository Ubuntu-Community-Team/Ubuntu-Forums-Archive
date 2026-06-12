---
title: "converting MKV to MP4 for use on Plex server"
date: 2016-01-03
forum: Multimedia Software
---

### Post by Troy_Piggins on 2016-01-03
Plex server doesn't seem to recognise MKV files, so I'm trying to convert them to MP4 files that I know work.  Plex website recommends MP4, H.264, 30fps, 8bit, AAC for max compatibility I think.  I've been searching around and see some recommendations to use something like ```
avconv -i input_file.mkv -codec copy output.mp4
```, but when I try this I get errors:
```
...
[mp4 @ 0x1daf3a0] track 0: could not find tag, codec not currently supported in container
...
Could not write header for output file #0 (incorrect codec parameters ?)
```

So I tried ```
avconv -i input_file.mkv -c:v libx264 -c:a aac output.mp4
``` but get:
```
...
[buffer @ 0x2273d60] Invalid pixel format string '-1'
Error opening filters!

```

Any tips?  All of this containers/codecs stuff is way over my head.

---

### Post by Yellow Pasque on 2016-01-04
So what kind of video/audio is actually in your mkv?
```
sudo apt-get install mediainfo
mediainfo input_file.mkv
```

Plex supposedly will transcode unsupported formats itself. [https://support.plex.tv/hc/en-us/articles/203810286-What-media-formats-are-supported-](https://support.plex.tv/hc/en-us/articles/203810286-What-media-formats-are-supported-)

---

### Post by Troy_Piggins on 2016-01-04
$ mediainfo input_file.mkv

> GeneralUnique ID                                : 211214885490128882012812617229213536485 (0x9EE681DC38EA67D59A54DDF5319290E5)
Complete name                            : input_file.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 250 MiB
Duration                                 : 51mn 54s
Overall bit rate                         : 673 Kbps
Encoded date                             : UTC 2015-11-23 14:11:37
Writing application                      : mkvmerge v4.0.0 ('The Stars were mine') built on Jun  5 2010 17:44:09
Writing library                          : libebml v1.0.0 + libmatroska v1.0.0
DURATION                                 : 00:51:51.765000000
NUMBER_OF_FRAMES                         : 72932
NUMBER_OF_BYTES                          : 24889056
_STATISTICS_WRITING_APP                  : mkvmerge v7.8.0 ('River Man') 32bit built on Mar 27 2015 16:18:02
_STATISTICS_WRITING_DATE_UTC             : 2015-11-22 12:52:38
_STATISTICS_TAGS                         : BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES


Video
ID                                       : 1
Format                                   : V_MPEGH/ISO/HEVC
Codec ID                                 : V_MPEGH/ISO/HEVC
Duration                                 : 51mn 54s
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 23.976 fps
Default                                  : No
Forced                                   : No


Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AAC / LC
Codec ID                                 : A_AAC
Duration                                 : 51mn 54s
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz / 24.0 KHz
Compression mode                         : Lossy
Default                                  : No
Forced                                   : No


Text
ID                                       : 3
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Default                                  : Yes
Forced                                   : No




---

### Post by FakeOutdoorsman on 2016-01-04
HEVC / H.265 can go in to MP4 container, but:

[list]
[*]I don't know anything about Plex or if it supports HEVC.
[*]avconv is buggy.
[/list]

If Plex does support it then [get a recent version of the real ffmpeg]("http://johnvansickle.com/ffmpeg/") then just re-mux:
```
ffmpeg -i input.mkv -c copy output.mp4
```

If not, then get ffmpeg and then re-encode the video and stream copy the audio:
```
ffmpeg -i input.mkv -c:v libx264 -c:a copy output.mp4
```

If you want to test instead of encoding the whole video just add "-t 60" for a 60 second output file duration.

---

### Post by andrew.46 on 2016-01-05
It is very much a side issue Troy but I see that your hevc video stream was muxed with mkvmerge 4.0.0:

```

Encoded date : UTC 2015-11-23 14:11:37
Writing application : **[COLOR="#FF0000"]mkvmerge v4.0.0[/COLOR]** ('The Stars were mine') built on Jun 5 2010 17:44:09
Writing library : libebml v1.0.0 + libmatroska v1.0.0

```

which is a little odd as mkvmerge did not really get proper hevc support until v6.8.0:

```

        * Released v6.8.0.

2014-02-28  Moritz Bunkus  <moritz@bunkus.org>

        * mkvmerge, mkvextract: new feature: added support for h.265/HEVC
        by merging the patches from DivX/Rovi Corp. So far HEVC is only
        supported as elementary streams and read from other Matroska
        files.

```

and I puzzle over the next couple of lines:

```

_STATISTICS_WRITING_APP :**[COLOR="#FF0000"] mkvmerge v7.8.0 ('River Man')[/COLOR]** 32bit built on Mar 27 2015 16:18:02

```

Changelog details [here]("https://mkvtoolnix.download/doc/ChangeLog"). Probably has no bearing on your issue though...

---

### Post by Yellow Pasque on 2016-01-05
> **FakeOutdoorsman said:**
> I don't know anything about Plex or if it supports HEVC.

Plex's changelog indicates it gained support for HEVC in version 0.9.10.0.

So what version of Plex do you have?

---

