---
title: "mpeg-2 to ogv with ffmpeg wont add meta data"
date: 2008-12-11
forum: Multimedia Software
---

### Post by phenest on 2008-12-11
If I try to convert an MPEG-2 to OGV with ffmpeg, it won't add meta data, e.g. -title.

Any ideas?

---

### Post by phenest on 2008-12-11
It seems ffmpeg won't add meta data to mpg's neither.

My solution was to use ffmpeg to convert to AVI (huge files though) adding any meta data. Then use OggConvert which preserves meta data. But this is long winded and can use a hell of a lot of hard drive space.

---

