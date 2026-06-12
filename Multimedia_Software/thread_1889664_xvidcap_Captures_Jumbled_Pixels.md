---
title: "xvidcap Captures Jumbled Pixels"
date: 2011-12-01
forum: Multimedia Software
---

### Post by Spaceman Spiff on 2011-12-01
Hello all,
  xvidcap and I are not getting along.  I am running Ubuntu 10,04 64 bit.  I am also using Jon Severinsson's ffmpeg/libavcodec daily PPA (since 10.04's version are outdated ... and just crap.)

  Installing xvidcap from Ubuntu Repo's works.  Except when I attempt to capture anytihng, I get a very jumbled picture.  It looks like giant vertical RGB pixels.

  So I decided perhaps it's because of my ffmpeg ppa, so I will install from source.  Source should work and use my newer avcodec right?!  Apparently not (it looks like it shipped with its own libraries, and compiled them even though I obviously have them installed.)  Furthermore, **compiling xvidcap failed.**  Below is the error message:

```

capture.c:68:35: error: X11/extensions/shmstr.h: No such file or directory
capture.c: In function ‘paintMousePointer’:
capture.c: In function ‘XGetZPixmap’:
capture.c:608: warning: large integer implicitly truncated to unsigned type
capture.c: In function ‘XGetZPixmapSHM’:
capture.c:668: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
capture.c:668: error: ‘req’ undeclared (first use in this function)
capture.c:668: error: (Each undeclared identifier is reported only once
capture.c:668: error: for each function it appears in.)
capture.c:669: error: ‘xShmGetImageReply’ undeclared (first use in this function)
capture.c:669: error: expected ‘;’ before ‘rep’
capture.c:675: error: ‘sz_xShmGetImageReq’ undeclared (first use in this function)
capture.c:675: error: ‘xShmGetImageReq’ undeclared (first use in this function)
capture.c:675: error: expected expression before ‘)’ token
capture.c:675: error: ‘X_ShmGetImage’ undeclared (first use in this function)
capture.c:693: error: ‘rep’ undeclared (first use in this function)

```

Could anyone PLEASE offer any suggestions.  Thank you for your time.

---

