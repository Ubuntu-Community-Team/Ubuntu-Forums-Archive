---
title: "TTCut - cutting DVB recordings"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by nattugglan on 2007-06-22
I'm looking for an app to cut DVB (MPEG2) recordings. MPEG2Schnitt (Windows) is perfect, but unfortunately displaying video does not work when running MPEG2Schnitt with WINE.

Has anyone installed TTCut on Ubuntu?

I've tried the .deb package (downloaded from ttcut.tritime.de), but it gives the following error.

```
Error: Dependency is not satisfiable: libc6
```
But libc6 & libc6-dev are already installed..

nattugglan

---

### Post by PeterKnaggs on 2007-06-22
Check out "xtscut", it's quite easy to build, and simple to use. It brings up a window showing the
I-frames and you can use the mouse scroll wheel to navigate to the cut points, then press the "e"
key to write out the "even" cuts. There's a man page for more info on options and keys. It's not
available as an Ubuntu package, but it's easy to build. On Ubuntu 7.04 Feisty Fawn it needs the
setting XLIB_SKIP_ARGB_VISUALS=1 before invoking xtscut (see [this bug]("https://bugs.launchpad.net/ubuntu/+source/imlib/+bug/70367") for details), like this:
```

XLIB_SKIP_ARGB_VISUALS=1 xtscut filename.ts
```
You can download the source code from [http://atscap.sourceforge.net]("http://atscap.sourceforge.net") and give it a try, it
has very few build dependencies: I think it's just
```
apt-get install imlib11-dev libmpeg2-4-dev freeglut3-dev
```
but I might have forgotten one. Of course, xtscut works best with ATSC files recorded
from over the air using atscap, for more info see the sourceforge page or my quickstart guide over [here]("http://www.penlug.org/twiki/bin/view/Main/DigitalTelevisionAtscap").

---

