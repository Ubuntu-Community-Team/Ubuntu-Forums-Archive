---
title: "MainActor and LiVES"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by WiseElben on 2006-12-23
Hi, MainActor's webpage states that it can import DivX, but when I try, it is read as an unknown media. Any ideas?

Since I had this problem in MainActor, I also tried to install LiVES, which led to more problems. "sudo aptitude install lives" gives me:

> 
The following packages have unmet dependencies:
  lives: Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed.
         Depends: libpango1.0-0 (>= 1.14.8) but 1.14.5-0ubuntu1 is installed.
         Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed.


When I try to install the newer version of libfontconfig1 (via a deb download), I am forced to upgrade another lib, which breaks everything.

Any.. like.. easy way of getting out of this? =)

---

