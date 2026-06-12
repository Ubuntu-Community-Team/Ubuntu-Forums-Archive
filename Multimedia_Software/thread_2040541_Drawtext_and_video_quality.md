---
title: "Drawtext and video quality"
date: 2012-08-11
forum: Multimedia Software
---

### Post by alfirdaous on 2012-08-11
Hello everybody,

I tried to add text into a video file, after encoding, I find out that the quality is lossy:

Original.mp4:
```

General
Complete name                    : ORIGINAL.mp4
Format profile                   : Base Media / Version 2
Codec ID                         : mp42
File size                        : 98.0 MiB
Duration                         : 21mn 2s
Overall bit rate                 : 651 Kbps


Video

Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Baseline@L3.0
Codec ID                         : avc1
Codec ID/Info                    : Advanced Video Coding
Duration                         : 21mn 2s
Bit rate mode                    : Variable
Bit rate                         : 553 Kbps
Maximum bit rate                 : 1 750 Kbps
Width                            : 640 pixels
Height                           : 360 pixels
Bits/(Pixel*Frame)               : 0.096
Stream size                      : 83.2 MiB (85%)


Audio

Duration                         : 21mn 2s
Bit rate mode                    : Variable
Bit rate                         : 96.0 Kbps
Maximum bit rate                 : 104 Kbps
Stream size                      : 14.5 MiB (15%)


```

Outfile.mp4:

```

General
Complete name                    : OUTFILE.mp4
Format profile                   : Base Media
Codec ID                         : isom
File size                        : 62.9 MiB
Duration                         : 21mn 2s
Overall bit rate                 : 418 Kbps
Writing application              : Lavf53.32.100


Video

ID                               : 1
Format                           : MPEG-4 Visual
Format profile                   : Simple@L1
Format settings, Matrix          : Default (H.263)
Codec ID                         : 20
Duration                         : 21mn 2s
Bit rate mode                    : Constant
Bit rate                         : 285 Kbps
Width                            : 640 pixels
Height                           : 360 pixels
Display aspect ratio             : 16:9
Colorimetry                      : 4:2:0
Bits/(Pixel*Frame)               : 0.050
Stream size                      : 42.9 MiB (68%)
Writing library                  : Lavc53.61.100
Encoded date                     : UTC 2012-07-18 20:54:53
Tagged date                      : UTC 2012-07-18 20:54:53


Audio

Duration                         : 21mn 2s
Bit rate mode                    : Constant
Bit rate                         : 127 Kbps
Sampling rate                    : 44.1 KHz
Stream size                      : 19.2 MiB (30%)
Encoded date                     : UTC 2012-07-18 20:54:53
Tagged date                      : UTC 2012-07-18 20:54:53

```


code used:

```

ffmpeg -y -i ORIGINAL.mp4 -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf':text='www.mywebsite.com':x=10:y=10:fontsize=20:fontcolor=white"  -vcodec libx264 OUTFILE.mp4

```

Thanks for your help

---

### Post by FakeOutdoorsman on 2012-08-13
By default libx264 in ffmpeg will use *-crf 23* if you do not declare a *-crf* value. This may not provide a sufficient output quality so you can add this option and lower the value until you achieve an acceptable output quality. Note that a value of *0* is lossless, but will create a huge file. I'm guessing that most people can't tell the difference between a value of *18* and the input.

My information applies only to ffmpeg from FFmpeg, not ffmpeg or avconv from libav which is what Ubuntu now uses.

---

### Post by alfirdaous on 2012-08-14
Thnx FakeOutdoorsman, I used this:

```

sudo ffmpeg -i INPUT.mp4 -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf':text='www.MySite.com':x=10:y=10:fontsize=20:fontcolor=white" -vcodec libx264 -crf 30 OUTPUT.mp4

```

Quality is good enough, the file size is lower by almost 40%

---

### Post by FakeOutdoorsman on 2012-08-14
You probably don't need to run ffmpeg with sudo. Also, if you're going to be playing the movies on a web site you should first process the ffmpeg output files with qt-faststart or MP4Box (part of the gpac package). These will move some data in the video so it can start playing before it is completely downloaded. See the [qt-fastart section](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide#qt-faststart) of [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) for an example, or if you want to install MP4Box:
```
sudo apt-get install gpac
```
...and then use MP4Box:
```
MP4Box -add ffmpeg-output.mp4 final-output-for-web.mp4
```
(However I prefer the lightweight simplicity of qt-faststart.)

---

### Post by alfirdaous on 2012-08-15
If it is for both usage, web and computer, is it the same way?

---

### Post by FakeOutdoorsman on 2012-08-15
You only need to use qt-faststart or MP4Box for the videos on the web if you're using something like a flash player. If users are simply downloading the video and playing them on their local player than there is no need to use qt-faststart or MP4Box, but it is fine if you do.

---

### Post by alfirdaous on 2012-08-16
So in case of using for both sides (web and to be downloaded)

---

### Post by FakeOutdoorsman on 2012-08-16
You can use the same file for both web playback and for download.

---

### Post by alfirdaous on 2012-08-16
that is a good and a new thing for me, second video does not change, but loading is fast, thx FakeOutdoorsman

---

### Post by alfirdaous on 2012-09-10
Sorry to come back in again, can we do this for other media files, especially MP3 files?

---

### Post by FakeOutdoorsman on 2012-09-11
Do you want to add a video stream with text to a MP3 file? Sorry, but I don't really understand what you would like to do.

---

### Post by alfirdaous on 2012-09-11
Sorry [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), I did not precise what I mean, the MP4Box option, really saved my time for loading videos, is there a way for MP3s' as well?? load the MP3 file fast as was done for the MP4s'

---

### Post by FakeOutdoorsman on 2012-09-11
> **alfirdaous said:**
> Sorry [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), I did not precise what I mean, the MP4Box option, really saved my time for loading videos, is there a way for MP3s' as well?? load the MP3 file fast as was done for the MP4s'

There is no need. The MP3 file should be able to play as it is downloading in a flash player; or at least it does for me using JW Player.

---

### Post by alfirdaous on 2012-09-11
> **FakeOutdoorsman said:**
> There is no need. The MP3 file should be able to play as it is downloading in a flash player; or at least it does for me using JW Player.

Oh, thank you, I am using [JW Player]("http://www.longtailvideo.com/") also

---

