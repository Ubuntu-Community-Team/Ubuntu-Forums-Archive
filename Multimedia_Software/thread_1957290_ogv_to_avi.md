---
title: "ogv to avi"
date: 2012-04-12
forum: Multimedia Software
---

### Post by gishaust on 2012-04-12
hi ubuntu lovers 

I am trying to create some screen casts about ubuntu and am having some trouble. I use myRecordDesktop and it works fine. The ogv gives prefect audio and video. 

The issue comes when I convert it to avi or mp4 it does not matter what I use I get the same result every time. I get perfect audio but the visual distorts as you can see from the image below.

Can anyone tell me why?

This is mencoder it works but the image distorts, I have also tried WinFF with the same result.
```

mencoder out.ogv -o ram.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000


```

I tried VLC and I got a good picture but no audio?

---

### Post by ron999 on 2012-04-12
Hi
Can you upload a short ogv sample file somewhere?

---

### Post by FakeOutdoorsman on 2012-04-12
MEncoder doesn't get much attention from developers anymore as far as I know. You could try ffmpeg directly:
```
ffmpeg -i input.org -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 output.avi
```
Lower qscale and aq values mean higher quality output. There was a time when ffmpeg could not decode recordmydesktop videos properly. I don't remember which versions of Ubuntu this affected. If it still gives you a bad output then you'll have to compile ffmpeg:

[How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by gishaust on 2012-04-12
Thanks for the replys

I have just tried ffmeg and got the same result 

here is an example of the issue

[http://www.purencool.com/video/](http://www.purencool.com/video/)
You will be able see the ogv is fine but after coding it into an avi  looks awful

---

### Post by gishaust on 2012-04-12
I went through How To Compile FFmpeg and x264 on Ubuntu tutorial and rebuilt the ffmpeg and it no converts to avi.

But I can only play it on my ubuntu box I move it to the windows machine an it says it can open the avi in media player when doing the transcoding I get this error

```
ffmpeg -i anewtrial.ogv -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 trialing.aviffmpeg version git-2012-04-12-4561feb Copyright (c) 2000-2012 the FFmpeg developers
  built on Apr 13 2012 07:55:14 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab
  libavutil      51. 46.100 / 51. 46.100
  libavcodec     54. 14.101 / 54. 14.101
  libavformat    54.  3.100 / 54.  3.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 67.101 /  2. 67.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0. 11.100 /  0. 11.100
  libpostproc    52.  0.100 / 52.  0.100
[ogg @ 0xae943a0] Broken file, keyframe not correctly marked.
Input #0, ogg, from 'anewtrial.ogv':
  Duration: 00:00:45.40, start: 0.000000, bitrate: 2348 kb/s
    Stream #0:0: Data: none
    Stream #0:1: Video: theora, yuv420p, 864x592 [SAR 1:1 DAR 54:37], 20 fps, 20 tbr, 20 tbn, 20 tbc
    Stream #0:2: Audio: vorbis, 22050 Hz, mono, s16, 89 kb/s
Please use -q:a or -q:v, -qscale is ambiguous
[buffer @ 0xaee17c0] w:864 h:592 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:flags=2
Output #0, avi, to 'trialing.avi':
  Metadata:
    ISFT            : Lavf54.3.100
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 864x592 [SAR 1:1 DAR 54:37], q=2-31, 200 kb/s, 20 tbn, 20 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 22050 Hz, mono, s16
Stream mapping:
  Stream #0:1 -> #0:0 (theora -> mpeg4)
  Stream #0:2 -> #0:1 (vorbis -> libmp3lame)
Press [q] to stop, [?] for help
[ogg @ 0xae943a0] Broken file, keyframe not correctly marked.
    Last message repeated 1 times
Broken file, keyframe not correctly marked.ime=00:00:09.80 bitrate=2367.3kbits/s    
Broken file, keyframe not correctly marked.ime=00:00:16.90 bitrate=3115.6kbits/s    
[ogg @ 0xae943a0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.ime=00:00:22.83 bitrate=3839.0kbits/s    
Broken file, keyframe not correctly marked.ime=00:00:29.91 bitrate=3976.3kbits/s    
[ogg @ 0xae943a0] Broken file, keyframe not correctly marked.
Broken file, keyframe not correctly marked.ime=00:00:36.17 bitrate=4089.0kbits/s    
Broken file, keyframe not correctly marked.ime=00:00:42.44 bitrate=4197.2kbits/s    
[avi @ 0xb0b9660] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1727 >= 1727
av_interleaved_write_frame(): Invalid argument


```

Can anyone help me

---

### Post by ron999 on 2012-04-12
> **gishaust said:**
> 

Can anyone help me

[COLOR="Red"][avi @ 0xb0b9660] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1727 >= 1727
av_interleaved_write_frame(): Invalid argument
[/COLOR]
This "monotonically" seems to be a bug with latest version of FFmpeg.
Try with **[COLOR="Red"].mp4[/COLOR]** istead of **.avi**

Hi
I've converted the ogv file using MEncoder and FFmpeg.
The new files don't play so well on my system, probably because they are 1216x720 and only a few seconds long.
But the video quality is good, not pixelated as in your original screenshot.
Your new FFmpeg will probably be OK when using [COLOR="Red"].mp4[/COLOR].(or **.mkv**)
And possibly your MEncoder is too old.

```
mencoder original.ogv -o new_mencoder.avi -oac mp3lame -lameopts fast:preset=standard -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=4000
```

```
ffmpeg -i original.ogv -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 new_ffmpeg[COLOR="Red"].mp4[/COLOR]
```

---

### Post by gishaust on 2012-04-12
ffmpeg -i original.ogv -vcodec mpeg4 -qscale 3 -acodec libmp3lame -aq 4 new_ffmpeg.mp4 now works thanks 

However on my windows machine it will not play except in VLC in the windows media player I get perfect picture but no sound. Is it the way I am encoding it?

---

### Post by ron999 on 2012-04-12
...

---

