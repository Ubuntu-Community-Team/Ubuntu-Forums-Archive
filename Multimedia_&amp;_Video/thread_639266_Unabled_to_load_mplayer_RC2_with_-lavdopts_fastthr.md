---
title: "Unabled to load mplayer RC2 with -lavdopts fast:threads=2"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by FallenGod on 2007-12-13
I'm using Ubuntu 7.10 and installed RC2 of mplayer through backports.  For some reason though, mplayer fails to load if I attempt to put -lavdopts fast:threads=2 into the .mplayer/config file to take advantage of multicore H264 decoding.

Anyone know why this might be?  The most CPU intensive thing I do anymore is watch HD video, and even with a E6750 high bitrate 1080 is dropping frames when I'm stuck on one core and can't use any lavdopts options.  The same video under windows will use only 50% of each core with CoreAVC, so I know it should be playable if I can take advance of both my cores.

---

### Post by sciurus on 2008-03-18
In the config file you shouldn't have the hypen before lavdopts.

---

### Post by KazMisMas on 2008-05-11
in the config it must be
lavdopts=fast=1:threads=2

---

