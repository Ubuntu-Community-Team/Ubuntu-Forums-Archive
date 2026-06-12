---
title: "ffmpeg: Unrecognized option 'same_quant' &amp; Failed to set value 'intermediate1.mpg"
date: 2012-04-28
forum: Multimedia Software
---

### Post by AlexOnVinyl on 2012-04-28
I don't know why I'm receiving this message but Im trying to combine two parts to a movie - but whenever I try using the FFmpeg FAQ - [http://ffmpeg.org/faq.html#How-can-I-join-video-files_003f]("http://ffmpeg.org/faq.html#How-can-I-join-video-files_003f")

So here's what I did: 

```
ffmpeg -i Se7en.1995.CD1.DVDRip.AC3.XviD.avi -same_quant intermediate1.mpg && ffmpeg -i Se7en.1995.CD2.DVDRip.AC3.XviD.avi -smae_quant intermediate2.mpg && cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg && ffmpeg -i intermediate_all.mpg -same_quant output.avi
```

and here's the output:

> Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (1000000/41709)
Input #0, avi, from 'Se7en.1995.CD1.DVDRip.AC3.XviD-CTRX.avi':
  Duration: 01:03:02.33, start: 0.000000, bitrate: 1530 kb/s
    Stream #0.0: Video: mpeg4 (Simple Profile), yuv420p, 640x272 [PAR 1:1 DAR 40:17], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s

Here's the error:

> [b]Unrecognized option 'same_quant'
Failed to set value 'intermediate1.mpg' for option 'same_quant'[/b]

Can anyone help me out?

---

### Post by evilsoup on 2012-04-28
Recent ffmpeg has changed the -sameq flag to -same_quant (because -sameq was confusing people I think). You are probably using an old version of ffmpeg, so try using -sameq instead of -same_quant.

---

### Post by ron999 on 2012-04-28
> **AlexOnVinyl said:**
>  but Im trying to combine two parts to a movie - but whenever I try using the FFmpeg... 

Can anyone help me out?
Hi
FFmpeg is the wrong tool for this job.
MEncoder is more suitable.
Like this:-
```
mencoder file1.avi file2.avi -ovc copy -oac copy -o output.avi
```

---

### Post by AlexOnVinyl on 2012-04-29
> **evilsoup said:**
> Recent ffmpeg has changed the -sameq flag to -same_quant (because -sameq was confusing people I think). You are probably using an old version of ffmpeg, so try using -sameq instead of -same_quant.

I got the latest ffmpeg from the Medibuntu repo, is there another source instead?

> **ron999 said:**
> Hi
FFmpeg is the wrong tool for this job.
MEncoder is more suitable.
Like this:-
```
mencoder file1.avi file2.avi -ovc copy -oac copy -o output.avi
```

Well, Im trying to learn ffmpeg more so than mencoder - also - do I have to use the cat command to make a caterized version first then make a final version?

---

### Post by AlexOnVinyl on 2012-04-29
Bump.

---

