---
title: "Remove 5.1 audio stream   from mp4"
date: 2009-03-12
forum: Multimedia Software
---

### Post by Lybic on 2009-03-12
Ok i  have an .mp4 video containing a 2 ch audio stream and a 5.1 stream. I know on windows I can use mp4muxer to de-multiplex the 5.1 out so it will stream to my  xbox,  but I am having a tough time figuring out how to to this in Linux. I don't want to re-encode the video(several hours) as this only takes a few minutes in windows to just remove the 5.1 stream. I dislike having to use my wife vista laptop for this ( it gives her a sense of winning lol)

I could be missing something very simple so  go easy on me

Thanx in advance

---

### Post by andrew.46 on 2009-03-12
Hi,

Ffmpeg can do this quite quickly. Can you run the following command on your file to show how the streams are mapped:

```
ffmpeg -i myfile.mp4
```

And then the syntax can be demonstrated to copy, rather than re-encode, the appropriate video and audio streams.

Andrew

---

### Post by Lybic on 2009-03-12
Andrew here is the output

```

 FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:41:23, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Test.mp4':
  Duration: 01:36:22.0, start: 0.000000, bitrate: 2666 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 720x400 [PAR 0:1 DAR 0:1], 12000.00 tb(r)
    Stream #0.1(und): Audio: mpeg4aac, 48000 Hz, stereo
    Stream #0.2(und): Audio: mpeg4aac, 48000 Hz, 5:1
Must supply at least one output file

```

hope this is what you needed and thanx for the reply
I  had a feeling i would use ffmpeg just not sure how

---

### Post by andrew.46 on 2009-03-12
Hi Lybic,

> **Lybic said:**
> 
```

Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Test.mp4':
  Duration: 01:36:22.0, start: 0.000000, bitrate: 2666 kb/s
[COLOR="Red"][B]    Stream #0.0(eng): Video: h264, yuv420p, 720x400 [PAR 0:1 DAR 0:1], 12000.00 tb(r)
    Stream #0.1(und): Audio: mpeg4aac, 48000 Hz, stereo
    Stream #0.2(und): Audio: mpeg4aac, 48000 Hz, 5:1[/B][/COLOR]

```

This is actually an easy one as by default FFmpeg will select the *first* video and the *first* audio stream, looks like your first audio stream is the one you are after so.....
```

ffmpeg -i Test.mp4 -vcodec copy -acodec copy another_Test.mp4
```

should copy the video stream and the stereo audio stream to a new container, omitting the second audio stream. If you actually wanted to use the second audio stream (the 5:1 stream) *then* you would use the -map syntax that I mentioned previously as follows:

```
ffmpeg -i Test.mp4 -map 0:0 -vcodec copy -map 0:2 -acodec copy yet_another.mp4
```

and while FFmpeg was processing the file you would see the message:

```
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.2 -> #0.1
```

that demonstrated FFmpeg changing the mapping of the output file.

Hope this helps,

Andrew

---

### Post by Lybic on 2009-03-13
Thank you Andrew this is exactly what i was looking for...

my life is made so much easier by this

thanx again

---

