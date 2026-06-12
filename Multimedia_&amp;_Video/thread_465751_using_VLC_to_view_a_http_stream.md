---
title: "using VLC to view a http stream"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-06-06
Hi,

I try to use VLC to view a http stream. It takes 3 minutes before anything start showing. I assume it start downloading all the content before displaying it.

But i try the same version of VLC on Windows XP on same machine with same stream, but it only takes 5 seconds. 

Can you please tell me why there is such a big difference? And if there is anything I can configure VLC so that it can stream http (view)?

Thank you.

---

### Post by madmetal on 2007-06-07
> **yinglcs2 said:**
> Hi,

I try to use VLC to view a http stream. It takes 3 minutes before anything start showing. I assume it start downloading all the content before displaying it.

But i try the same version of VLC on Windows XP on same machine with same stream, but it only takes 5 seconds. 

Can you please tell me why there is such a big difference? And if there is anything I can configure VLC so that it can stream http (view)?

Thank you.

maybe different settings? look at buffer settings..
also give a try to open vlc from terninal using sudo vlc and see if its better..

---

### Post by abakker on 2007-06-12
The cause appears to be Feisty's version of ffmpeg which VLC uses to play Flash video. It seems there is a bug in reading the flash video header.  Apparently the Windows version is compiled against a newer ffmpeg that does not have this problem.

I've found no quick solution for this, you could upgrade ffmpeg as per
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

and then do something similar for VLC, as that has to be recompiled too.

---

### Post by yinglcs2 on 2007-06-12
Thanks.

---

