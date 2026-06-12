---
title: "mplayer -vf perspective, what is it supposed to do?"
date: 2011-01-22
forum: Multimedia Software
---

### Post by josvanr on 2011-01-22
I'm trying to use my webcam (resolution 1600x1200) to display a
document (rectangle shape). I want the
document to fill the entire mplayer window. The webcam is placed a bit
above the
document so it is displayed as a trapezium shape. The corner points of
the trapezium
in the 1600x1200 image are:

(274,57 ) top left
(1368,18 ) top right
(449,947 ) bottom left
(1287,918 ) bottom right

So I figured, use -vf perspective to map these corners to the edges of
the mplayer window e voila,
the entire screen is filled up with the entire document:

 mplayer tv:// -tv
driver=v4l2:width=1600:height=1200:device=/dev/video1 -fps 15 -vf
perspective=274:57:1368:18:449:947:1287:918:0


The 3 sides (left/top/right of the document do  seem to be more or less
ligned up with the edges of the mplayer window in this way,
but unfortunately, the bottom 30% of the area indicated by the points
is *not displayed*
when I give this command.

So maybe there is a bug, or I'm stretching the filter beyond its
capability, or I just don't understand
how it works. Any help would be appreciated!


josvanr

---

