---
title: "Calculation bitrate from ffmpeg parameters  tbr tbn tbc ??"
date: 2010-03-06
forum: Multimedia Software
---

### Post by rahul23 on 2010-03-06
hi all
  Is it possible to calculte video bitrate from ffmpeg parameters tbr , tbn , tbc ??
 can anyone explain what these parameters really are ??

I am building a php program which needs video bitrate , audio bitrate information , but some of the times ffmpeg does not ouputs bitrate but it always show these parameters information.

Thanks in advance.

---

### Post by rahul23 on 2010-03-08
anyone !!

---

### Post by FakeOutdoorsman on 2010-03-08
These parameters refer to "time base":
[[FFmpeg-user] What does the output of ffmpeg mean? tbr tbn tbc etc?](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2009-May/020425.html)

You may find the command-line version of [mediainfo](http://mediainfo.sourceforge.net/en) to be more verbose in displaying bitrate information than FFmpeg.

---

