---
title: "setting aspect ratio for dv files"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by Jacky_J on 2008-03-22
So i made a movie in cinelerra from 16:9 dv files.  There's some bug in cinelerra where if you use certain filters or fading the exported dv file is 4:3 instead of 16:9.

Two questions:

1. Is there a work around for this bug in cinelerra?

2. If not, i'm trying to reset the aspect ratio manually using:

mencoder in.dv -oac copy -ovc copy -aspect 16:9 -force-avi-aspect 16:9 -o out.dv

However that doesn't work. Anyone know how to reset the aspect ratio of a dv file?

Thanks

---

