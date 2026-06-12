---
title: "How to join(combine) two .ogv files into one?"
date: 2010-11-27
forum: Multimedia Software
---

### Post by jiapei100 on 2010-11-27
Hi, all:

How to use ffmpeg or memcoder to join two .ogv files into a single .ogv ??
Let's suppose the first .ogv video file is named as "01.ogv" and the resolution is 800*600;
the second .ogv video file is named as "02.ogv" and the resolution is 720*576.

I'd love to join two video files into a whole one, with the resolution 320*240.
How to?

Thank you very much in advance.


Best Regards
JIA Pei

---

### Post by FakeOutdoorsman on 2010-11-27
There are several methods to do this, but since you want to change the sizes of the inputs, which requires re-encoding, there will be some extra steps.

1. Re-encode the video of the first input into a format that is *cat* friendly:
```
ffmpeg -i input1 -an -vcodec mpeg2video -qscale 1 -vf scale=320:-1 out1-v.mpg
```
2. Re-encode the second input. The *scale* and *pad* filters will be used to resize the input and preserve the aspect ratio:
```
ffmpeg -i input2 -an -vcodec mpeg2video -qscale 1 -vf scale=-1:240,pad=320:0:10:0 out2-v.mpg
```
3. Output audio:
```
ffmpeg -i input1 out1-a.wav
ffmpeg -i input2 out2-a.wav
```
4. Combine the video with *cat*:
```
cat out1-v.mpg out2-v.mpg > out3-v.mpg
```
5. Combine the audio with *cat*:
```
cat out1-a.wav out2-a.wav > out3-a.wav
```
6. Re-encode everything into ogv:
```
ffmpeg -i out3-v.mpg -i out3-a.wav -vcodec libtheora -qscale 3 -acodec libvorbis -aq 5 output.ogv
```

Your FFmpeg may be too old to use the scale and pad filters. If yes, then you can try the *-s* and *-pad** options instead, or compile a more recent FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

I made a command for each step so it may be easier to understand, but these steps can be optimized by using named pipes to avoid intermediate files as shown here:
[url=http://www.ffmpeg.org/faq.html#SEC27]
FFmpeg FAQ: 3.15 How can I join video files?[/url]

---

