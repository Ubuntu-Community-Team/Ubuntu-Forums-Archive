---
title: "ffmpeg - problem with codecs when resizing"
date: 2011-01-18
forum: Multimedia Software
---

### Post by sombrancelha on 2011-01-18
Hello,

I'm trying to resize some videos, since I'll watch them on my phone and I want to save space.

The videos are .avi and I was using the following command to resize:

```
ffmpeg -i 1.avi -s 399x225 Movie1.avi
```

It worked very well for the first videos. However, for some of them I got the following error message:
```

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997003/125000)
Input #0, avi, from '23.avi':
  Metadata:
    ISFT            : transcode-1.0.6
  Duration: 00:43:02.42, start: 0.000000, bitrate: 1136 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, 2 channels, s16, 128 kb/s
[COLOR="Red"][mpeg4 @ 0x8db86d0]timebase not supported by mpeg 4 standard[/COLOR]
Output #0, avi, to 'Movie23.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 399x225 [PAR 1:1 DAR 133:75], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, 2 channels, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

I noticed that for the videos that re-encoded nicely, there was a ISFT field for the output data, while in the above one there isn't. It was Lavf52.64.2

I think it's a codec encoding issue, but I'm not sure. Anyway, if anyone knows what's wrong and how to solve it, I'd appreciate very much.

Thank you

---

### Post by gordintoronto on 2011-01-18
Try this, courtesy of Fakeoutdoorsman:

ffmpeg -i input.mp4 -vcodec mpeg4 -map_meta_data 0:0 -s 480x320 -acodec libfaac output.m4v

(Note that you must first cd to the folder where the input file resides.)

---

### Post by sombrancelha on 2011-01-18
> **gordintoronto said:**
> Try this, courtesy of Fakeoutdoorsman:

ffmpeg -i input.mp4 -vcodec mpeg4 -map_meta_data 0:0 -s 480x320 -acodec libfaac output.m4v

(Note that you must first cd to the folder where the input file resides.)

Hmmm... My output can't be m4v, my phone (Android) doesn't play m4v.

---

### Post by FakeOutdoorsman on 2011-01-19
Those are some strange looking numbers (2997003/125000).  I know nothing of the Android, but you can try this for those troublesome inputs:
```
ffmpeg -i 1.avi -s 399x225 -qscale 4 -acodec copy -r 23.98 Movie1.avi
```
[indent]**-qscale 4:** Replaces the default *-b 200k* for a higher quality video.
**-acodec copy:** "copy and paste" the audio instead of re-encoding.
**-r 23.98:** force a frame rate instead of trying to use the broken values from the input.[/indent]
Might go out of sync, but it's worth a try.

---

### Post by andrew.46 on 2011-01-20
Depending on the exact model of your android phone you might be interested to know that most modern android devices can playback mp4 files with h.264 video and aac sound, which means you can search out and use Fakeoutdoorsman's FFmpeg guide on these forums. Only addition required to the guide is that you will need to add in the baseline preset, for example:

```
-vpre slow -vpre baseline
```

This certainly works well on my HTC Legend and I believe it also works on the phone's big brother the HTC Desire.

---

