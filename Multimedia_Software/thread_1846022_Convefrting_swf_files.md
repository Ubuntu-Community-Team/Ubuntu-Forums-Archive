---
title: "Convefrting swf files"
date: 2011-09-18
forum: Multimedia Software
---

### Post by asai on 2011-09-18
Hi

I'm trying to convert a swf file to avi.
The swf file is created from multible jpg files with this command:
```
jpeg2swf *.jpg -o movie.swf
```

Then I use ffmpeg like this:
```
ffmpeg -i movie.swf movie.avi
```

But I get this error message:
```
picture size invalid (0x0)
```

Any suggestions to where I go wrong?

---

