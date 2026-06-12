---
title: "FFMPEG: &quot;Unknown encoder 'h264'&quot;"
date: 2011-05-30
forum: Multimedia Software
---

### Post by !CoffeeTable on 2011-05-30
I've search these forums and Google for the last day but haven't found a solution for this problem.

I have a raw .dv file named "dvgrab-001.dv". My command is
```
ffmpeg -i dvgrab-001.dv -acodec faac -vcodec h264 -f flv test.flv
```

My the output I receive is
```
[dv @ 0x9a36bc0]Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from 'dvgrab-001.dv':
  Duration: 00:00:15.34, start: 0.000000, bitrate: 28771 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480, 28771 kb/s, PAR 40:33 DAR 20:11, 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Unknown encoder 'h264'
```

Output from ```
ffmpeg -formats | grep 264
``` is
```
DE h264            raw H.264 video format
  E ipod            iPod H.264 MP4 format
```

In Synaptic Package Manager if I filter for 264 I have the packages "x264" and "libx264-106" installed (along with some other scripts).

---

### Post by ron999 on 2011-05-30
Hi
Try with -acodec **libfaac** -vcodec **libx264**

---

### Post by gordintoronto on 2011-05-30
Or you could install WinFF and avoid the command line.

---

### Post by !CoffeeTable on 2011-05-31
> **ron999 said:**
> Hi
Try with -acodec **libfaac** -vcodec **libx264**

I'm pretty sure this won't work... I've tried h.264, x264, and libx264 extensively. I'll give it a shot with the libfaac though.

[QUOTE=gordintoronto]Or you could install WinFF and avoid the command line.[/QUOTE]

My goal is to pipe dvgrab output into ffmpeg and out to an RTMP server. "dvgrab-001.dv" is the output from dvgrab so this is an initial test to make sure both components are functioning independently.

---

### Post by !CoffeeTable on 2011-05-31
> **ron999 said:**
> Hi
Try with -acodec **libfaac** -vcodec **libx264**


Sorry for the double post.

Using -acodec libfaac and -vcodec libx264 worked.


Thank you!

---

### Post by gordintoronto on 2011-05-31
> **!CoffeeTable said:**
> My goal is to pipe dvgrab output into ffmpeg and out to an RTMP server. "dvgrab-001.dv" is the output from dvgrab so this is an initial test to make sure both components are functioning independently.

I don't think dvgrab and ffmpeg put their video output files on stdout, so you're not actually piping, just stacking commands.

---

### Post by !CoffeeTable on 2011-06-01
> **gordintoronto said:**
> I don't think dvgrab and ffmpeg put their video output files on stdout, so you're not actually piping, just stacking commands.

Dvgrab manpage actually says using '-' as base causes Dvgrab to use stdout (dvgrab - causes the raw video data to be printed in the terminal if you want to check). Though its not really in the documentation, FFMpeg also uses '-' as an argument for '-i' to indicate stdin in input.

You can test reading stdin with:
```
cat dvgrab-001.dv | ffmpeg -i - -acodec libfaac -vcodec libx264 -vpre default -f flv test.flv
```


So yes, it is actually piped.

---

### Post by gordintoronto on 2011-06-01
Interesting, thanks!

---

