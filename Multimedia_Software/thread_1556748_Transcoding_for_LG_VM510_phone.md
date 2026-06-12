---
title: "Transcoding for LG VM510 phone"
date: 2010-08-19
forum: Multimedia Software
---

### Post by nutznboltz on 2010-08-19
I could not find any advice for how to transcode video for the LG VM510 "Rumor Touch" phone.

So far I've been able to come up with this:

```
ffmpeg -i input.xxx -f mp4 -vcodec mpeg4 -b 192k -acodec libfaac -ab 128k -s 320x240 output.mp4 
```

Where "input.xxx" is the input file be it "input.avi" or "input.flv" or whatever.

The results playback on the LG VM510 device by using
Main Menu -> Tools -> File Manager

The results are slightly choppy.

I have a batch of old MP4's I converted for Blackberry World Edition 8830 that play on the LG VM510 "Rumor Touch" phone.  I lost the script that I used to generate them since it was back in 2008.

If you have any other working examples or advice about what to try to optimize please post them.  Thanks.

---

### Post by roy913 on 2010-08-20
have you tried the program called WinFF which has an option for LG phone?

---

