---
title: "Problem with VLC"
date: 2011-03-17
forum: Multimedia Software
---

### Post by Enigmapond on 2011-03-17
Hi!

I was recently running vlc-110 from falk-t-j repository when it crashed and I was unable to get it working again. I deleted everything VLC from my system and installed the one from the normal repo and it also crashes on start. Here is the output:

```
gazon@Gazon2~ $ vlc -v
VLC media player 1.0.6 Goldeneye
[0x9394b8] main libvlc warning: could not open plugins cache file /home/gazon/.cache/vlc/plugins-04081e.dat for reading
[0xa86848] qt4 interface warning: This should not happen 20
[0xa86848] qt4 interface warning: This should not happen 19
[0xa86848] qt4 interface warning: This should not happen 20
WARNING: QApplication was not created in the main() thread.
Segmentation fault
```

Any suggestions on how to make it work would be greatly appreciated.

Cheers!

---

### Post by mc4man on 2011-03-17
Not sure what falk-t-j repository you were using  - if it was the DEPRECATED PPA that had 450+ packages then you've likely upgraded other packages including the shared ffmpeg libs
(a good example of a ppa that is quite likely eventually screw up your install
If not too late you might consider using ppa-purge

The vlc-110 package is a very 'odd' package - installed to /opt more like a make install than a debian package set.

---

