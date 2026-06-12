---
title: "remove graphical tearing on intel graphics"
date: 2008-05-31
forum: Multimedia Software
---

### Post by gruffy-06 on 2008-05-31
Screen tearing is annoying. You may notice program windows torn horizontally as you drag them or video playback is not smooth. This may not be a major problem for some, but users have trouble trying to resolve this issue themselves. At the moment, there exists a solution for Intel cards for eliminating tearing in apps that use OpenGL, except Compiz. This is only known to work on the latest Intel drivers and was tested on an Intel 915GM on version 8.04 of Ubuntu.

Removing the screen tearing involves two steps. The first is to install the *driconf* package from the *universe* repository. Secondly, run *driconf*. Change the vertical synchronisation setting so that it always uses it. Tearing has been successfully removed!

Post here if you have any further problems.

---

