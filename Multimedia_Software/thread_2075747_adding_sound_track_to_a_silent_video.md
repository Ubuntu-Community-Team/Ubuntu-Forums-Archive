---
title: "adding sound track to a silent video"
date: 2012-10-24
forum: Multimedia Software
---

### Post by George Heine on 2012-10-24
Trying to make a simple video.  The audio is a song, and the "video" is a static image displaying the words to the song.

Was able to create a simple video with avconv by:
```
avconv -i stanza1_%03d.jpg 1sec.avi
cat 1sec.avi 1sec.avi 1sec.avi > 3secraw.avi
cat 3secraw.avi 3secraw.avi  3secraw.avi >9secraw.avi
 avconv -i 9secraw.avi 9sec.avi

```where "stanza1_%03d.jpg" was 25 copies of a jpeg image with the words of the song.

The audio track is also nine seconds long (used sox with the "trim" command).   Put the audio in WAV format  (44100 samples/sec, 16 b/sample, 2 channels), on the hope or guess that most software would support it.  

Here's what happens when trying to merge the audio and video:
```

$ avconv -i 9sec.avi -i 9sec.wav test.avi
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
Input #0, avi, from '9sec.avi':
  Metadata:
    encoder         : Lavf53.21.0
  Duration: 00:00:09.00, start: 0.000000, bitrate: 638 kb/s
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 1024x767 [PAR 1:1 DAR 1024:767], 25 tbr, 25 tbn, 25 tbc
[wav @ 0x96282e0] max_analyze_duration reached
Input #1, wav, from '9sec.wav':
  Duration: 00:00:09.00, bitrate: 1411 kb/s
    Stream #1.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
[buffer @ 0x971f0c0] w:1024 h:767 pixfmt:yuv420p
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[ac3 @ 0x96c8720] channel_layout not specified
[ac3 @ 0x96c8720] No channel layout specified. The encoder will guess the layout, but it might be incorrect.
[ac3 @ 0x96c8720] invalid bit rate
Output #0, avi, to 'test.avi':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: mpeg4, yuv420p, 1024x767 [PAR 1:1 DAR 1024:767], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: ac3, 44100 Hz, stereo, flt, 200 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 -> mpeg4)
  Stream #1:0 -> #0:1 (pcm_s16le -> ac3)
Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height

```In examining this output, it looks like I need to specify some parameters for the audio stream, but not sure what to put.   Or should the input audio be reformatted?   Any suggestions?

Thanks for any help -

---

### Post by shantiq on 2012-10-24
```
avconv -i 9sec.avi -i 9sec.wav [COLOR="Red"]-c copy[/COLOR] test.avi
```


Hi George got this info a few days back from FakeOutdoorsman for ffmpeg


just tested it with avconv and works the same

---

### Post by FakeOutdoorsman on 2012-10-24
Here is another method using just one image:
```
ffmpeg -loop 1 -i input.jpg -i input.wav -shortest output.avi
```

I'm assuming the 25 images from "stanza1_%03d.jpg" were all the same.

This will use the default video and audio settings which may or may not be what you want. This next example will output H.264 video and MP3 audio into MKV (Matroska) container (who needs AVI these days?):

```
ffmpeg -loop 1 -i input.jpg -i input.wav -c:v libx264 -preset slow -tune stillimage -crf 24 -c:a libmp3lame -q:a 4 -shortest output.mkv
```

See the CRF section in the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for more details.

I don't use avconv, so you may have to use ffmpeg (the real one, not the forked version in the repo) for this to work. You can compile it ([instructions](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)), use [Jon Severinsson's FFmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), or get an easy to use static binary from the [FFmpeg download](http://ffmpeg.org/download.html) page.

---

### Post by George Heine on 2012-10-25
Thanks to both Shantiq and Fake Outdoorsman for your quick replies.  I was able to get both  "-c copy" and "-loop 1" working with ffmpeg 0.8.3 from the repo.  The -loop option is especially handy; saves cluttering the disk with multiple copies of a static image.  

Thanks also to Fake Outdoorsman for his llink to the ffmpeg compile instructions.   I used to have an older compiled-from-source version of ffmpeg  (in response to one of his  earlier posts), but it was wiped out in a recent conversion to Ubuntu 12.04.   

Will try a fresh compile in the next day or two and report back.

---

### Post by George Heine on 2012-10-26
Both of FakeOutdoorman's solutions worked after compiling ffmpeg with x264, AAC, VP8.  The compiled version also permits video filtering effects such as horizontal flip, something I was looking for in a[COLOR=Magenta] [previous post]("http://ubuntuforums.org/showthread.php?t=1949713") .[/COLOR] 

To my eye, the MKV video does not look different from the AVI, but it uses only about 25% as much space; perhaps this is the effect of "-tune stillimage".

Guess the next step is to learn more about those video and audio settings....

---

### Post by FakeOutdoorsman on 2012-10-26
> **George Heine said:**
> To my eye, the MKV video does not look different from the AVI, but it uses only about 25% as much space

FFmpeg by default uses the "mpeg4" encoder for .avi, while it uses libx264 (if available) for .mkv. These are two different video formats and libx264 is much more efficient--also its default settings are more sane.

---

