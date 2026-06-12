---
title: "64bit mp4 conversion performance"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by Robocoastie on 2007-01-19
Hi all,

I timed last night VLC converting a 40 minute mpeg file (This weeks smallville ep - commercials) and in Windows XP Media Center it took 22 minutes to convert.

This afternoon I tried the same file in edgy64bit and it also took 22 minutes.

Is perhaps the VLC version I installed the 32bit one or is the lack of performance a kernel problem (using the generic default one)?

edit/update: aha, I think there isn't a special 64bit version now that I look closer at the VLC website it mentions SSE2 extensions supported but nothing about a 64bit optimized version, that would be the reason the performance is the same I guess. Time to find another program if I want to keep comparing performance.

---

### Post by kd7swh on 2007-01-19
that is still slow. have you tried doing the conversion with ffmpeg. I have found it is faster.

( you would have to compile it to get mpeg4 support like i did)


EDIT: an upgrade to dapper  or edgy may help too. Dapper ran 25% faster than Breezy and Edgy runs 50% faster than dapper did for me.

---

### Post by Robocoastie on 2007-01-19
I'm running edgy (just haven't updated my signature yet). hmm how do I convert with ffmpeg? I thought that was just a codec to install.

thanks

edit/add: I found this to aid me: [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

conversion using the script there after installing with those steps took 14 minutes, but it was at a lesser resolution so I suspect if I did it at 640x480 it would be 22 minutes again. It also had the audio-video out of sync whereas it wasn't with VLC in either Windows XP MCE, or edgy.

I wonder if the "legal" ones from Fluendo (see fluendo.com) are faster

---

### Post by kd7swh on 2007-01-19
If you have videos that are out of sync you can use mencoder to sync them.


```
mencoder -forceidx -oac copy -ovc copy input.avi -o output.avi 
```

---

