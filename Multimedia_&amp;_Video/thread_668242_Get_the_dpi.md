---
title: "Get the dpi"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by mehturt on 2008-01-15
How to get the current DPI?
I'm getting different results from xrdb and xdpyinfo:

$ xdpyinfo |grep reso
  resolution:    108x108 dots per inch
$ xrdb -query | grep dpi
Xft.dpi:        80

---

### Post by GodsMadClown on 2008-01-29
So am I.
```

$ xrdb -query | grep Xft.dpi
Xft.dpi:        96
$ xdpyinfo |grep reso
  resolution:    75x75 dots per inch

```

---

