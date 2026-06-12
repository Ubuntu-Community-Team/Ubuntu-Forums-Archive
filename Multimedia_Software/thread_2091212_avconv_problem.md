---
title: "avconv problem"
date: 2012-12-04
forum: Multimedia Software
---

### Post by msknight on 2012-12-04
Hi Folks,

Ubuntu 64 bit 12.04

Source file is a "MOD" from a Canon camcorder. It's an odd proprietary format which shoots in 1028 but actually works by stretching 820 pixels.

Anyway, for some time I've been converting it using avconv using a bitrate of something like this...

avconv -i MOV001.MOD -b 3000000 -ac 2 -ar 44100 mov001.m4v

I had to do a rebuilt yesterday and now I'm having problems.
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3


Now, that produces an error on the bitrate being too high but even though I take it to nearly the max I can, I still end up with a smaller size and a blockier image than I did before.

New attempts include...
 -b 550k
-crf 50

No improvement. They still look rubbish. I've even tried two passes

Looking at the codecs in VLC, they all come out as they did before...

Codec: MPEG-4 Video (mp4v)
Decoded format: Planar 4:2:0 YUV

I don't know what has happened as a result, but the end result is really blocky and unacceptable.

---

### Post by evilsoup on 2012-12-04
Well, I don't know about bitrates (the problem *might* be that you should use the new -b:v flag instead of -b), but with -crt, for x264 (which is the default encoder for MP4 files), lower numbers are better, 18 is 'visually lossless', 0 is completely lossless and 28 is generally about as high as you should go for decent-quality video. See [here]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide"), it's an ffmpeg guide, but it applies just as well to avconv.

Actually, wait... your first example is a bitrate of 3 million, whereas the other example is 550 thousand... so maybe try a higher video bitrate. Or a lower crt value.

EDIT: also, your needs might be better suited by Handbrake, which is a very nice GUI frontend for avconv. You'd need the version from [this PPA](https://launchpad.net/~stebbins/+archive/handbrake-releases), if you want to use it. Obviously, there are benefits to using avconv on the commandline (slightly easier batch processing, it's better documented for all sorts of little fine-tuning things), but I don't think you're using those particularly so...

---

### Post by msknight on 2012-12-04
Thanks for that. If I go to 600k, I get an error. I can't actually reach the 3 mill I used before.

Even at 600k I get...

[aac @ 0xa61d40] Too many bits per frame requested
Output #0, mp4, to 'MOV046.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-31, 600 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16, 600 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video -> mpeg4)
  Stream #0:1 -> #0:1 (ac3 -> aac)
Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by msknight on 2012-12-04
I tried a -crf 5 and that's turning out the same result.

Am I missing something else from my command please?

---

### Post by evilsoup on 2012-12-04
Aah, I see the problem.

In previous verison of ffmpeg/avconv, the -b flag set the bitrate for the video stream; in more recent versions, if you use -b then that will set the bitrate for *all* streams to that level. AAC audio tops out at 320 kb/sec, so that's why avconv is throwing up an error.

Try using -b:v instead of -b; this will set the video bitrate to whatever level you choose, while leaving the audio alone. You should be able to set it to three million, if you want.

You would almost certainly be better off using crf, as it almost always offers better quality. It looks like avconv isn't using libx264 by default (I thought it did, but then I always set the codecs manually out of habit). I would suggest using:

```
avconv -i MOV001.MOD -c:v libx264 -crf 18 -preset medium -c:a libfaac -ac 2 -ar 44100 -b:a 192k mov001.m4v
```

Although, unless you're short on HDD space or have specific needs, you could keep the AC3 audio as-is - which means no loss of audio quality. That would use this:

```
avconv -i MOV001.MOD -c:v libx264 -crf 18 -preset medium -c:a copy mov001.m4v
```

---

### Post by msknight on 2012-12-04
I think that -b:v seems to have done the trick!  I think this is going to work.  The output file is so far growing at a reasonable rate.

Many thanks!

---

