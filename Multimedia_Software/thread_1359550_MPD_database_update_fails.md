---
title: "MPD database update fails"
date: 2009-12-19
forum: Multimedia Software
---

### Post by ronzo on 2009-12-19
When I try to run an mpd db update it fails - no matter if I initially create the db file or if I try to update my old one.

MPD quits with a segmentation fault (everytime at the same file - if I delete that file, mpd quits somewhere else. Filetype seems to be irrelevant)

I am using karmic and therfore mpd 0.15.4.

I found a bug that could be the problem I am experiencing:
[http://musicpd.org/mantis/view.php?id=2111#bugnotes](http://musicpd.org/mantis/view.php?id=2111#bugnotes) (already closed cause it was not reproduceable)

Any tips/hints/...?

I filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/498994](https://bugs.launchpad.net/ubuntu/+bug/498994)

---

### Post by ronzo on 2010-01-05
A defective .ram-file caused the trouble. After removing it, everything worked like a charm.

---

