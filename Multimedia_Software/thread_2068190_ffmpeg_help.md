---
title: "ffmpeg help"
date: 2012-10-08
forum: Multimedia Software
---

### Post by frenzen on 2012-10-08
ffmpeg -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi -acodec libfaac -b:a 128k -vcodec mpeg4 -b:v 1200k -flags +aic+mv4 output.mp4

[avi @ 0xa6a3500] non-interleaved AVI
Input #0, avi, from 'Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi':
  Duration: 01:32:00.55, start: 0.000000, bitrate: 3807 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 1280x720 [SAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0:1: Audio: ac3 ([0] [0][0] / 0x2000), 48000 Hz, 5.1(side), s16, 448 kb/s

I am trying to make this file small and mp4 with aac 48000 hz, can anyone help me? 

ffmpeg -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi
Julia X 2011 720p BRRip XVID AC3-TRiNiTY
File: Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi
Size: 2627287924 bytes (2.45 GiB), duration: 01:32:00, avg.bitrate: 3808 kb/s
Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Video: mpeg4, yuv420p, 1280×720, 23.98 fps(r)

I've tried with the first code but the quality turned 2 be crap

im using ubuntu 10.04 with 2gb ram server

---

### Post by FakeOutdoorsman on 2012-10-08
> **frenzen said:**
> I am trying to make this file small and mp4 with aac 48000 hz, can anyone help me?

mp4 is a container format and can utilize several formats including H.264 and MPEG-4 Part 2 video. Do you know what video format you need?

---

### Post by TheFu on 2012-10-08
To make an xvid/avi file smaller, it is usually a good idea to reduce the resolution.  I've never had luck trancoding from xvid to h.264 directly.  I've always gone through mpeg2 first.  There might be a way to do what you want directly.

The easiest way that I've found to get to a good mpeg2 format, is to use presets.
$ ffmepg -target ntsc-dvd -i input.avi output.mpg

Then I'd use handbrakeCLI to convert to h.264 from mpeg2.  The handbrake GUI has presets for common devices, if that's your real motive for trying to reduce the file size.

---

### Post by frenzen on 2012-10-08
> **FakeOutdoorsman said:**
> mp4 is a container format and can utilize several formats including H.264 and MPEG-4 Part 2 video. Do you know what video format you need?

yes i want h.264 with audio aac 48000 hz with stereo

> **TheFu said:**
> To make an xvid/avi file smaller, it is usually a good idea to reduce the resolution.  I've never had luck trancoding from xvid to h.264 directly.  I've always gone through mpeg2 first.  There might be a way to do what you want directly.

The easiest way that I've found to get to a good mpeg2 format, is to use presets.
$ ffmepg -target ntsc-dvd -i input.avi output.mpg

Then I'd use handbrakeCLI to convert to h.264 from mpeg2.  The handbrake GUI has presets for common devices, if that's your real motive for trying to reduce the file size.


there is no easier way just 2 do it once?

---

### Post by FakeOutdoorsman on 2012-10-08
> **TheFu said:**
> I've never had luck trancoding from xvid to h.264 directly.  I've always gone through mpeg2 first.

I've never heard of such issues. What exactly is the problem? Re-encoding to a lossy output as an intermediate file is usually not recommended.

> **frenzen said:**
> yes i want h.264 with audio aac 48000 hz with stereo

Try this:
```
ffmpeg -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi -c:a libfaac -q:a 100 -c:v libx264 -crf 24 -preset medium output.mp4
```

Important options are *-crf* and *-preset*. See the CRF section of the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for details.

You can encode short random sections to get an idea of the quality if you don't want to encode the whole thing using the **-ss** (skip *x* time from beginning) and **-t** (duration) options:

```
ffmpeg -ss 00:05:30 -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi -t 30 -c:a libfaac -q:a 100 -c:v libx264 -crf 24 -preset medium output.mp4
```

If you are targeting a specific output file size then see the [Two-Pass](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#twopass) section of the encoding guide for examples and more information.

---

### Post by frenzen on 2012-10-08
> **FakeOutdoorsman said:**
> I've never heard of such issues. What exactly is the problem? Re-encoding to a lossy output as an intermediate file is usually not recommended.



Try this:
```
ffmpeg -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi -c:a libfaac -q:a 100 -c:v libx264 -crf 24 -preset medium output.mp4
```

Important options are *-crf* and *-preset*. See the CRF section of the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for details.

You can encode short random sections to get an idea of the quality if you don't want to encode the whole thing using the **-ss** (skip *x* time from beginning) and **-t** (duration) options:

```
ffmpeg -ss 00:05:30 -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi -t 30 -c:a libfaac -q:a 100 -c:v libx264 -crf 24 -preset medium output.mp4
```

If you are targeting a specific output file size then see the [Two-Pass](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#twopass) section of the encoding guide for examples and more information.

the 33 seconds is a very good quality. trying the whole thing will tell u the results

[http://grab.by/gCga](http://grab.by/gCga)

EDIT: can you give me another code cuz for 3 mins its already 40 mb so ill end up with 1.3 gb? I pmed u

---

### Post by TheFu on 2012-10-08
> **FakeOutdoorsman said:**
> I've never heard of such issues. What exactly is the problem? Re-encoding to a lossy output as an intermediate file is usually not recommended.

Audio sync is the usual issue, but poor quality has resulted too.  To be honest, I've avoided the single-step method for a very long time unless I just needed a temporary file for a specific device that only supported non-HiDef content, so it might not be an issue any longer.

That is a good idea to use 2-pass encoding. I'd completely forgotten about that.  I used mencoder before swtiching to HandBrakeCLI.

---

### Post by FakeOutdoorsman on 2012-10-08
> **frenzen said:**
> EDIT: can you give me another code cuz for 3 mins its already 40 mb so ill end up with 1.3 gb? I pmed u

For a three minute output use *-t 00:03:00* or *-t 180*. Note that using one-pass crf will not allow you to easily guess the output size since various sections of the video will require more or less bits to reach your desired quality level (as set with *-crf*). To generalize: use crf if quality is your main concern, or two-pass if a specific output file size is more important.

---

### Post by frenzen on 2012-10-08
> **FakeOutdoorsman said:**
> For a three minute output use *-t 00:03:00* or *-t 180*. Note that using one-pass crf will not allow you to easily guess the output size since various sections of the video will require more or less bits to reach your desired quality level (as set with *-crf*). To generalize: use crf if quality is your main concern, or two-pass if a specific output file size is more important.

3 mins is = 42.9 mb
1 min = 14.3 mb
93 mins = 1329.9 mb

anyone other code for 720p but smaller size

so im trying this right now 

ffmpeg -ss 00:05:30 -i Julia.X.2011.720p.BRRip.XVID.AC3-TRiNiTY.avi -t 30 -c:a libfaac -q:a 100 -c:v libx264 -crf 24 -preset slow output2.mp4
10.9 mb = 30 seconds even more than the medium output

---

### Post by frenzen on 2012-10-10
> **FakeOutdoorsman said:**
> For a three minute output use *-t 00:03:00* or *-t 180*. Note that using one-pass crf will not allow you to easily guess the output size since various sections of the video will require more or less bits to reach your desired quality level (as set with *-crf*). To generalize: use crf if quality is your main concern, or two-pass if a specific output file size is more important.

I tried superslow but the file is very big. Can you give me some other codes from avi to mp4 but to make the file at least 600-700 mb?

---

### Post by FakeOutdoorsman on 2012-10-10
> **frenzen said:**
> I tried superslow but the file is very big. Can you give me some other codes from avi to mp4 but to make the file at least 600-700 mb?

See the [two-pass example](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide#twopass) in the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

---

