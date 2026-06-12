---
title: "dvgrab 3.0 in gutsy"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by ibedonc on 2007-11-21
when I do dvgrab - | mplayer -

dvgrab fail to output to stdout as per docs and creates a -001.avi

what am I missing ?

---

### Post by ibedonc on 2007-11-21
I tried a older from from another distro and it works , but I need features from 3.0

---

### Post by James Paige on 2008-01-22
I had the same problem. when I run:
```
dvgrab - | mplayer -
```
I get -001.avi in the current directory. The workaround I found was to use the -format raw command-line argument:
```
dvgrab -format raw - | mplayer - -demuxer lavf -lavfdopts format=dv
```

Although i do not know *why* that works :(

---

