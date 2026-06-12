---
title: "combining 4:3 and 16:9 titles with dvdauthor"
date: 2014-03-20
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2014-03-20
Hey guys.

Usually, when I author DVDs from compliant mpg's, I use the following commands:

```
dvdauthor -o dvd -t video1.mpg video2.mpg -t video3.mpg video4.mpg
export VIDEO_FORMAT=NTSC
dvdauthor -o dvd -T
genisoimage -dvd-video -o dvdimage.iso dvd
```

However, this only seems to work when all the video*.mpg files are the same aspect ratio.  What if I want my first title to be 4:3, and my second title to be 16:9?

I have heard this is possible by creating different "titlesets." But, how would I do that?

Any help would be much appreciated.  Thanks!

---

