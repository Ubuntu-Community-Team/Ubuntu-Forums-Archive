---
title: "ffmpeg .vob to .avi on ubuntu server 10.10"
date: 2010-12-17
forum: Multimedia Software
---

### Post by Arcath on 2010-12-17
I have a .vob file that has been ripped from a dvd, when I watch the .vob its very good quality video and 5.1 english audio but when I use ffmpeg it has rubbish video and mono french audio.

That was using this command:

> ffmpeg -i /samba/ripping/vobs/12161840#2.vob -f avi /samba/ripping/avis/test.avi

I've tried a few different variations on that but it never comes back with anything good just bigger files with bad video and incorrect sound.

I know the videos good and the correct audio streams exist so how do I select a 5.1 track and get good video?

ffmpeg gives the .vob details as:

> Input #0, mpeg, from '/samba/ripping/vobs/12161840#2.vob':
   Duration: 00:42:05.56, start: 0.287267, bitrate: 5738 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 8436 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.3[0x82]: Audio: ac3, 48000 Hz, mono, s16, 192 kb/s
Output #0, avi, to '/samba/ripping/avis/test.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp2, 48000 Hz, mono, s16, 64 kb/s
Stream mapping:
   Stream #0.0 -> #0.0
   Stream #0.3 -> #0.1

I may not have the librarys required for good conversion installed but ideally what i'm going for is use of the good soundtrack and little to no loss of video quality.

---

### Post by Arcath on 2010-12-17
I have now been able to use the example command in the ffmpeg docs:

> ffmpeg -i /samba/ripping/vobs/12161840#2.vob -f avi -vcodec mpeg4 -b 800k -g 300 -bf 2 -acodec libmp3lame -ab 128k /samba/ripping/avis/test.avi

The video is better, still makes it non widescreen though. but no matter what I tweak it always goes for the mono french soundtrack not the nice 5.1 english ones

---

### Post by FakeOutdoorsman on 2010-12-17
You can tell FFmpeg which video and audio streams you want to use with the **-map** option:
```
ffmpeg -i input -map 0:0 -map 0:1 [output options] output
```
The numbers refer to the video and audio streams in your file:
```
Stream **#0.0**[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 8436 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
Stream **#0.1**[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
Stream #0.2[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
Stream #0.3[0x82]: Audio: ac3, 48000 Hz, mono, s16, 192 kb/s
```
I'm not sure if the English track is 0.1 or 0.2.  Is there a particular output format you want?

---

### Post by Arcath on 2010-12-17
> **FakeOutdoorsman said:**
> You can tell FFmpeg which video and audio streams you want to use with the **-map** option:
```
ffmpeg -i input -map 0:0 -map 0:1 [output options] output
```
The numbers refer to the video and audio streams in your file:
```
Stream **#0.0**[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 8436 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
Stream **#0.1**[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
Stream #0.2[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
Stream #0.3[0x82]: Audio: ac3, 48000 Hz, mono, s16, 192 kb/s
```
I'm not sure if the English track is 0.1 or 0.2.  Is there a particular output format you want?

thanks, that did work but i'm getting closer to the result I want with mencoder now. just tweaking the video and audio settings for the "perfect" result

---

