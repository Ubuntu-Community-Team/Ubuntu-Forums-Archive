---
title: "ffmpeg 0:5.1 from kprn ppa de-installed during last updates"
date: 2010-08-10
forum: Multimedia Software
---

### Post by orion940 on 2010-08-10
When I upgraded this morning, the upgrades caused ffmpeg to be de-installed.  I have the Korn ppa in the sources.  I went back to re-install ffmpeg (4:0.6.1~ppa) and got these messages:

ffmpeg:
 Depends: libavcodec52 but it is not going to be installed or
     libavcodec-extra-52 (>=4:0.6) but 4:0.5.1-1ubuntu1+medibuntu1 is to be installed
  Depends: libavdevice52 (>=4:0.6-1~ppa1) but 4:0.5.1-1ubuntu1 is to be installed or
     libavdevice-extra-52 but it is not going to be installed
 Depends: libavfilter1 but it is not going to be installed or
     libavfilter-extra-1 (>=4:0.6) but it is not installable
 Depends: libavfilter1 but it is not going to be installed or
     libavfilter-extra-1 (<4:0.6-99) but it is not installable
  Depends: libavformat52 (>=4:0.6-1~ppa1) but 4:0.5.1-1ubuntu1 is to be installed or
     libavformat-extra-52 but it is not going to be installed

If I remove the korn ppa, everything will resolve ok when I go to install ffmpeg 0.5.1.  

Has anyone see this as well? Is there a fix or do I need to just wait a day or two til things catch up?

---edit---
fixed..it looks like ffmeg was removed from the korn ppa.
--- end edit---

O.

---

