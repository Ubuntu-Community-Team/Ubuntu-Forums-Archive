---
title: "WinFF Can't Find ffplay"
date: 2009-11-13
forum: Multimedia Software
---

### Post by rchar66 on 2009-11-13
I compiled ffmpeg from source using the directions found on these forums. I also installed WinFF. When I try to use WinFF to convert some video files, I get an error saying WinFF can't find ffplay?

How do I get ffplay installed? It's not in the repo's.

I'm running 9.10 Karmic.

Richard

---

### Post by mc4man on 2009-11-13
If you built ffmpeg as described in F.O's how to then ffmpeg and ffplay are in /usr/local/bin
winff defaults to /usr/bin for both so open winff's preferences and make the changes for both

---

### Post by FakeOutdoorsman on 2009-11-13
This is a known WinFF bug.  It will probably be fixed in the next release:

[Issue 56: Add /usr/local/bin for FFplay executable search](http://code.google.com/p/winff/issues/detail?id=56)

---

### Post by rchar66 on 2009-11-14
That did the trick! Thank you to both of you for your replies and for the steps to compile ffmpeg.

Richard

---

