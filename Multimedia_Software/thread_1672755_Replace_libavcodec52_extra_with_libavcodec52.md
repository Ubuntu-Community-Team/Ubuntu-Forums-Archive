---
title: "Replace libavcodec52 extra with libavcodec52"
date: 2011-01-21
forum: Multimedia Software
---

### Post by DanneStrat on 2011-01-21
Hi! I have a question:

I have the ubuntu restricted extras package installed.

If you find an application in the repositories that

need the libavcodec52 package to be installed and the libavcodec52 

extra package to be removed, could you safely do that?

What is the difference between libavcodec52 and libavcodec52 extra?

Thanks.

---

### Post by mc4man on 2011-01-21
> If you find an application in the repositories that

need the libavcodec52 package to be installed and the libavcodec52

extra package to be removed, could you safely do that?
For the most part sure - there are a few app's that may require the extra version, if they were installed they'd also be removed.

The extra versions extend some encoding support thru libavcodec

Most packages that depend on libavcodec would/should allow either to satisfy the dependency - if not that's a flaw in that particular package.

---

### Post by ajgreeny on 2011-01-21
The "extra" packages are needed for ffmpeg to encode to certain restricted formats, but not to decode them.  So if you use ffmpeg to produce mp3 files, form example, you need the extra versions of some of the libav* packages.

As mc4man says, I think either the standard or the extra package will satisfy the dependencies of most if not all the packages in Ubuntu.

---

### Post by DanneStrat on 2011-01-24
OK!

Thanks for your help!

---

