---
title: "ffmpeg help (Mp4 to AVI and aac to ac3)"
date: 2010-02-09
forum: Multimedia Software
---

### Post by hoffman462 on 2010-02-09
Hello,
I'm trying to copy a video file from mp4 to avi, in the process I need to convert aac to ac3 audio.

I've researched this for a few days, and I think I'm on the right track but need some help.

I typed, and received:
```

ffmpeg -i inputfile.mp4
...

    Stream #0.0(und): Video: h264, yuv420p, 1280x720, 23.98 tbr, 23.98 tbn, 47.95 tbc
    Stream #0.1(und): Audio: aac, 48000 Hz, 5.1, s16

```

I then tried the following command by carefully studying some examples on ffmpeg online:

```

ffmpeg -i 'inputfile.mp4' -aspect 16:9 -sameq -vcodec libxvid -acodec ac3 -ac 6 'outputfile.avi'

```

My resulting avi file causes many issues in a variety of players, I'm clearly doing something incorrect, can someone please lend some advice?

Thank you very much.

---

### Post by warp99 on 2010-02-09
Try this string:

```
ffmpeg -i input.mp4 -vcodec mpeg4 -acodec ac3 -ar 48000 -ab 192k -ac 6 -sameq -aspect 16:9 output.avi
```

---

### Post by hoffman462 on 2010-02-10
hello,
thank you very much,
the command that you listed above seems to work well.

I appreciate your help.

---

### Post by FakeOutdoorsman on 2010-02-10
> **warp99 said:**
> Try this string:

```
ffmpeg -i input.mp4 -vcodec mpeg4 -acodec ac3 -ar 48000 -ab 192k -ac 6 -sameq -aspect 16:9 output.avi
```

I recommend using *-qscale* instead of *-sameq*.  I'm not sure if you can use qscale effectively with H.264 video because it's quantizer scale is too different than everything else.  A good balance for a qscale value is 3-5 and 2 is roughly visually lossless.

---

### Post by TheMadGeneral on 2011-05-07
Yep that did the trick for me. Thanks

---

