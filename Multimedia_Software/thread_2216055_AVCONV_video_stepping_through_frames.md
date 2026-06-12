---
title: "AVCONV video stepping through frames"
date: 2014-04-09
forum: Multimedia Software
---

### Post by jus-gagnon on 2014-04-09
I've been trying to convert a vob file of a movie I bought recently and everytime I watch it the video seems as if it is stepping through frame by frame. This is driving me nuts since I was able to convert it simply with handbrake GUI with no issues at all. I prefer to use command line because Im weird like that. I have run into this issue a few times before with other videos. 

Here is the commands Im using, nothing fancy.
avconv -i Hobbit.vob -vcodec libx264 -crf 20 -preset slow -acodec copy Smaug.mp4

Here is the file input:

aadrik@aadrik-Satellite-L505:~$ avconv -i HOBBIT_DESOLATION_OF_SMAUG_D11.vob
avconv version 0.8.10-6:0.8.10-0ubuntu0.13.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:53:28 with gcc 4.8.1
[mpeg @ 0x9a6a20] max_analyze_duration reached
Input #0, mpeg, from 'HOBBIT_DESOLATION_OF_SMAUG_D11.vob':
  Duration: 00:07:11.09, start: 0.045500, bitrate: 140749 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 23.98 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x82]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.3[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.4[0x83]: Audio: ac3, 0 channels
At least one output file must be specified


Any help would be great since I am losing my mind here.

---

### Post by andrew.46 on 2014-04-09
avconv can be a little troublesome at times and the repository version almost always a little dated. Have a look at this guide and then run your command with the latest FFmpeg:

[https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide)

Interesting to see if the results are superior...

---

### Post by jus-gagnon on 2014-04-09
Thanks so much that worked like a charm. Any idea on why avconv didnt work?

---

### Post by andrew.46 on 2014-04-09
> **jus-gagnon said:**
> Thanks so much that worked like a charm. 

Thanks are better given to FakeOutdoorsman whose work on these Forums ended up on this wiki :).

> Any idea on why avconv didnt work?

Good to hear that the latest FFmpeg fixed the issue! I don't use avconv myself as I have historically always used FFmpeg before and after the avconv fork arrived on the scene so it is difficult for me to comment. And I certainly don't want to be involved in the nasty and often vindictive politics of the split! Suffice to say that for me FFmpeg is the superior product and best used directly from git; you have now had first hand experience of this...

---

### Post by jus-gagnon on 2014-04-09
Yeah the only reason I switched was because I saw the message saying that ffmpeg was outdated and to use avconv. Thanks so much for the help.

---

### Post by andrew.46 on 2014-04-09
> **jus-gagnon said:**
> Thanks so much for the help.

My pleasure :).

---

