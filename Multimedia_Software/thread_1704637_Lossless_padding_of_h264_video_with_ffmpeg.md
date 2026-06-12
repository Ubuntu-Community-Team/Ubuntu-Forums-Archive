---
title: "Lossless padding of h264 video with ffmpeg"
date: 2011-03-10
forum: Multimedia Software
---

### Post by seanlano on 2011-03-10
I have some videos in an mkv container that are 1920 pixels wide, but less than 1080 pixels high. This causes problems when playing the videos on a PS3 (after converting to an AVCHD system), because the PS3 won't centre the video, leaving a very large black bar at the bottom but none at the top. Is there a way to use mencoder or ffmpeg to losslessly add padding to the top and bottom to make the video 1920x1080? 

If I use ```
ffmpeg -i video.mkv -acodec copy -vcodec copy -scodec copy -padtop 132 -padbottom 132 out.mkv

``` then ffmpeg won't do the padding, and the resulting file is basically exactly the same. If I use ```
ffmpeg -i video.mkv -acodec copy -vpre libx264-lossless_fast -scodec copy -padtop 132 -padbottom 132 out.mkv

``` I get ```
Output #0, matroska, to 'anr.mkv':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0(eng): Video: mpeg4, yuv420p, 1920x1080 [PAR 45:34 DAR 40:17], q=10-51, 200 kb/s, 1k tbn, 23.98 tbc
    Stream #0.1(eng): Audio: 0x2001, 48000 Hz, 6 channels
    Stream #0.2(eng): Subtitle: 0x0000
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.2 -> #0.2
Press [q] to stop encoding
[mpeg4 @ 0xf31330]me_method is only allowed to be set to zero and epzs; for hex,umh,full and others see dia_size
Video encoding failed

```


Any ideas?

---

### Post by FakeOutdoorsman on 2011-03-11
You need to re-encode if you want to add padding to a video, so any pad options used with *-vcodec copy* will be ignored. Of course some players can add padding upon playback, but I doubt the PS3 will let you do that.

Your second command didn't work because you forgot *-vcodec libx264* which is a requirement when using the libx264 presets.
```
ffmpeg -i input -vcodec libx264 -vpre lossless_fast -padtop 132 -padbottom 132 -threads 0 -acodec copy -scodec copy output
```
Note that these pad options have been depreciated for the pad filter in newer FFmpeg.

---

