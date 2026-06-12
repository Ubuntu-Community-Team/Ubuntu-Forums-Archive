---
title: "mplayer-nogui problems such as requires X?"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Potatoj316 on 2008-08-20
Im trying to install mplayer-nogui on a computer that does not have X.  I would like my computer to continue not having X on it so thats why I chose mplayer-nogui.  I know for a fact that mplayer can run in the terminal and play audio but I dont understand why when I try to install it that it tries to bring in X11 dependencies as well.  (such as x11-utils) 

I tried this
```
aptitude show mplayer-nogui
```
and it didnt say that mplayer needed those X packages so one of mplayer's dependencies must have a dependency that uses X, but why?  Is there a way to stop this?  I tried removing the x packages by using - x11-utils (for a bunch of them) at the (Y/n/?) prompt but it just made things look worse.

---

