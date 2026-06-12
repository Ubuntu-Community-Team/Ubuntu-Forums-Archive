---
title: "Xorg freeing invalid memtype"
date: 2010-07-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-07-12
I've been watching my system log files lately and notice this one is happening quiet often. Anyone know what its related to?

I'm using the Nvidia Current drivers with dual monitors in Twinview.
X.Org X Server 1.8.1.902 (1.8.2 RC 2)
Release Date: 2010-06-21

```

[   20.404724] Xorg:1119 freeing invalid memtype e0000000-e0001000
[   23.823002] Xorg:1119 freeing invalid memtype d0fe0000-d0ff9000
[  221.778618] Xorg:1119 freeing invalid memtype d2590000-d25d8000
[  231.491109] Xorg:1119 freeing invalid memtype d2590000-d25e0000
[  286.830913] Xorg:1119 freeing invalid memtype d27db000-d2c1a000
[  766.915209] Xorg:1119 freeing invalid memtype d1c88000-d1d78000
[  768.662156] Xorg:1119 freeing invalid memtype d1c88000-d1d78000
[  774.947042] Xorg:1119 freeing invalid memtype d0a11000-d0a82000
[  808.785337] Xorg:1119 freeing invalid memtype d0a11000-d0a32000
[ 2637.142082] Xorg:1119 freeing invalid memtype d1b21000-d1d22000
[ 3220.568402] Xorg:1119 freeing invalid memtype d1b21000-d1d22000
[ 9736.437470] Xorg:1119 freeing invalid memtype d0c23000-d0c2c000
[11502.662992] Xorg:1119 freeing invalid memtype d0c7b000-d0c8c000
[11888.928369] Xorg:1119 freeing invalid memtype d0c9c000-d0cb6000
[12079.498828] Xorg:1119 freeing invalid memtype d38e0000-d3de1000

```

I'm not seeing any visual problems from it, but I'd like to fix this if possible.

---

