---
title: "ffmpeg, problems when cropping video"
date: 2011-02-18
forum: Multimedia Software
---

### Post by havok1977 on 2011-02-18
Ok, I have been struggling with this for a few hours now and i need to ask for some help. 

I am trying to convert some 4:3 PAL VOB video files to 16:9 NTSC DVD compliant, and I figure the best way to do it is to first crop the necesary black space in order to have the proper aspect ratio before converting the frame rate.

These are my current video file stats:

```
Input #0, mpeg, from 'eng-VTS_01_1.VOB':                                                     
  Duration: 00:27:25.64, start: 1.000000, bitrate: 4974 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 9300 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s

```

I am trying to do the cropping like this:

```
ffmpeg -i eng-VTS_01_1.VOB  -vf crop=704:396:10:90 -acodec copy -vcodec copy -sameq neweng-VTS_01_1.VOB
```

Now, I have two problems with this command, first of all the output file is not cropped at all! Its just a plain copy of the original. And i figure its because I am specifing 'copy' for the video codec... am I right?

Working on that assumption i change the command to this:

```
ffmpeg -i eng-VTS_01_1.VOB  -vf crop=704:396:10:90 -acodec copy -vcodec mpeg2video -sameq neweng-VTS_01_1.VOB                                                                             
```

Which DOES actually output a cropped video, but the encoding is far from lossless, can anyone here suggest a sure way to get it done with the best possible quality?


PS. I also tried the -croptop, -cropbottom commands to find they are no longer supported:
```
Option 'croptop' has been removed, use the crop filter instead
```

---

### Post by FakeOutdoorsman on 2011-02-18
You can't crop without re-encoding. That's why *-vcodec copy* didn't seem to work for you. If you want it to be lossless then you'll need to use a lossless encoder such as x264 lossless, huffyuv, ffvhuff, or ffv1, for example. These output huge files.

Alternatively you could use a low enough *-qscale* that it will appear visually lossless. A value of *-qscale 2* with FFmpeg's MPEG-1/2/4 encoders can be considered roughly visually lossless. A higher value is lower quality, and 3-5 is a good balance between quality and file size.

---

### Post by havok1977 on 2011-02-19
> **FakeOutdoorsman said:**
> You can't crop without re-encoding. That's why *-vcodec copy* didn't seem to work for you. If you want it to be lossless then you'll need to use a lossless encoder such as x264 lossless, huffyuv, ffvhuff, or ffv1, for example. These output huge files.


Yeah that kind of figures, since what I want to do would ideally not involve a different codec, just MPEG2 to MPEG2 I kind of hoped it could be possible.

> **FakeOutdoorsman said:**
> 
Alternatively you could use a low enough *-qscale* that it will appear visually lossless. A value of *-qscale 2* with FFmpeg's MPEG-1/2/4 encoders can be considered roughly visually lossless. A higher value is lower quality, and 3-5 is a good balance between quality and file size.

I'll have to experiment with that parameter and see how it works, I really want to maintain the original quality as much as possible within the same file size range and keep things DVD compliant, as changing codecs would not be good for my purposes. 


Would you know of any other parameter that might help? Perhaps using -b for specifying the bitrate can bring something? If anyone can share some knowledge on the pros/cons of using either parameter Id appreciate it.

Thanks for your input

---

