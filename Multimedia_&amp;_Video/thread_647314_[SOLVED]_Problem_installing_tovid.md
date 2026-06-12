---
title: "[SOLVED] Problem installing tovid"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by whazooo on 2007-12-22
Tring to install tovid

well really tring to install the dependencies.

when trying to install mjpegtools I get this:

mjpegtools:
 Depends: libmjpegtools0 but it is not going to be installed
 Depends: libquicktime0 (>=0.9.10+debian) but it is not installable

I can install libmjpegtools0c2a
but after compiling tovid
at the prompt
#tovid
I get:
```

=========================================================
  mplex       MISSING!
=========================================================
  mpeg2enc    MISSING!
=========================================================
  yuvfps      MISSING!
=========================================================
  yuvdenoise  MISSING!
=========================================================
  ppmtoy4m    MISSING!
=========================================================
  mp2enc      MISSING!
=========================================================
  jpeg2yuv    MISSING!

```
You are missing CORE tovid dependencies! Please install the above MISSING 
dependencies and try again. See tovid.wikia.com/wiki/Tovid_dependencies or 
tovid.org for help.

I went to these websites but I couldnt find help for my specific problem
Any insights?
Thanks

here is my sourses list

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://www.debian-multimedia.org stable main
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse

```

---

### Post by z0mbie on 2007-12-22
Here are some deb packages for tovid:

[http://tovid.sourceforge.net/download/ubuntu/](http://tovid.sourceforge.net/download/ubuntu/)

---

### Post by whazooo on 2007-12-22
> **z0mbie said:**
> Here are some deb packages for tovid:

[http://tovid.sourceforge.net/download/ubuntu/](http://tovid.sourceforge.net/download/ubuntu/)
Thanks for the reply.

I tried those deb files and they wouldnt work.
I get the same error


mjpegtools:
Depends: libmjpegtools0 but it is not going to be installed
Depends: libquicktime0 (>=0.9.10+debian) but it is not installable

---

### Post by whazooo on 2007-12-25
I kept getting this:
```
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I removed libmjpegtools0c2a
and all went well

---

