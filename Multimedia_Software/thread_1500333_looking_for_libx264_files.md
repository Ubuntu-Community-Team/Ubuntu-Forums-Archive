---
title: "looking for libx264 files"
date: 2010-06-03
forum: Multimedia Software
---

### Post by Mia1990 on 2010-06-03
Dumb question i know but were do i get the .dev files for libx264 0.98 i think is the version it is asking for.I install the latest libx264 from git or does that install the .dev file also.
Thanks

---

### Post by Yellow Pasque on 2010-06-03
32-bit:
[http://www.debian-multimedia.org/dists/unstable/main/binary-i386/](http://www.debian-multimedia.org/dists/unstable/main/binary-i386/)
64-bit:
[http://www.debian-multimedia.org/dists/unstable/main/binary-amd64/](http://www.debian-multimedia.org/dists/unstable/main/binary-amd64/)

Install libx264-98 first, then libx264-dev. I know it's a debian site, but I looked at the package requirements and see no reason they won't install on lucid.

---

### Post by FakeOutdoorsman on 2010-06-03
> **Mia1990 said:**
> Dumb question i know but were do i get the .dev files for libx264 0.98 i think is the version it is asking for.I install the latest libx264 from git or does that install the .dev file also.
Thanks

If you're compiling FFmpeg then compile and install x264 from git.  This method will provide the necessary files.  For more information on compiling x264 and FFmpeg on Ubuntu:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Mia1990 on 2010-06-05
Thank you both.Yes i i just compiled the newest ffmpeg from svn and all went great.I never use the quick menu option in tovid so i do not need the vhooks.

---

