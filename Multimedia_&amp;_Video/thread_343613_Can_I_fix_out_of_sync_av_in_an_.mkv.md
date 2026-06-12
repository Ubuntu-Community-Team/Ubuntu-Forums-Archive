---
title: "Can I fix out of sync a/v in an .mkv?"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by HIGHLIFE on 2007-01-21
Hey I have a .mkv with out of sync a/v, and I was wondering if it's possible to sync them, and if so how?

---

### Post by Shatrat on 2007-01-21
Did you create the .mkv or is it something you downloaded?
I'm not an expert by any means but I think if it is authored incorrectly I dont think there is a way around it but to re-rip and create a new container.  You might want to check out some multimedia forums like doom9 or something.
Good luck.

---

### Post by majoridiot on 2007-01-22
```
mencoder -oac copy -ovc copy -o outputfile.avi inputfile.mkv
```

replacing of course, the proper filenames.  from there, you can load the resulting avi file into
avidemux and fiddle with the synch.

---

### Post by superm1 on 2007-03-04
Are you sure its the file itself out of sync?

I have been experimenting with transcoding HDTV MPEG2 recordings to mkv containers with h264/ac3.

I thought I was going crazy with how much I tweaked options and tried different resolutions, different filters - everything I could possibly think of.  

The audio is out of sync on mplayer and xine.  VLC won't play the files - it can't keep up.  
I brought the files over to a buddy with VLC on a mac and another with VLC on windows.  Works perfectly on both of their boxes.

I thought oh, maybe a bug in x264.  I upgraded to feisty - got the new x264 libraries, new VLC, new mplayer, new xine.  All the same.

---

### Post by bulyst on 2007-03-13
I've experienced the same problem on the mkv files with 720p H264 contents with mplayer. I noticed the out of sync a/v is intermittent. It is out of sync for a while and it will be okay after that.  I also found out that it consumed a lot of cpu power when playing those mkv files. Once I overclocked my Pentium D805 to 3Ghz, the situation became must better. However, once a while, out of sync a/v still occurred. 

There are also some tweaks on mplayer to fix the out of sync problem . According to the following url,

[http://freshmeat.net/articles/view/747/](http://freshmeat.net/articles/view/747/)

You can use -async 30 or enable the RTC to fix the sync problem. However, I tried both of them and they didn't really work for me. 

When I enabled RTC to fix the sync on a/v;

echo 1024 > /proc/sys/dev/rtc/max-user-freq

it even hanged mplayer whatever materials I played. I needed to use crtl - C to stop it.

Anyone experienced the same problem?

---

