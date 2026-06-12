---
title: "[SOLVED] IBM thinkpad t40 xorg.conf file (Radeon 7500 direct rendering)"
date: 2008-05-04
forum: Multimedia Software
---

### Post by xfceuser on 2008-05-04
(xubuntu 8.04)
IBM thinkpad T40 (Radeon M 7500)

I see a lot of post concerning the "direct rendering" of OpenGL, that does not work for me. Graphics are so slow and:
$  glxinfo | grep "direct rendering"    result:
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

and 

$  glxinfo | grep vendor 
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

I think the trick is in the correct xorg.conf file. Does anybody know where can I find the minimal file that will make "direct rendering" work (i try many posts but no luck). I think there must be a data base of these files for every popular system, such that one does not need to understand all details to make things work.

---

### Post by xfceuser on 2008-05-31
hi, i made this thread to help this for all who have the same problem,
[http://ubuntuforums.org/showthread.php?t=814518](http://ubuntuforums.org/showthread.php?t=814518)

the problem is also solved in the mentioned thread.

---

