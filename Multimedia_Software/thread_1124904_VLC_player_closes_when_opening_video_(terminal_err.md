---
title: "VLC player closes when opening video (terminal error included)"
date: 2009-04-13
forum: Multimedia Software
---

### Post by xJoo Unitx on 2009-04-13
When I open a video in VLC player, the window immediately closes.  I can open VLC player and use the interface to find a movie, but when I click on it, VLC closes... when I open VLC with the terminal, and then try and open a video, i get this error... any idea how to get around this?



[????????] x11 video output error: X11 request 143.31 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  31 (X_GLXCreateWindow)
  Serial number of failed request:  52
  Current serial number in output stream:  53
Locking assertion failure.  Backtrace:



sorry if the solution is simple, I'm a little new with this

---

### Post by cwall on 2009-04-14
Confirmed, but sadly, no workaround.

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743)

---

