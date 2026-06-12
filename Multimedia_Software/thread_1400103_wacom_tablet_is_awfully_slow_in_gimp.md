---
title: "wacom tablet is awfully slow in gimp"
date: 2010-02-06
forum: Multimedia Software
---

### Post by v923z on 2010-02-06
Hi All,

I was wondering whether someone could help me out with this problem. In short, I have a Wacom Bamboo Fun 6x8 tablet, and I could set it up (well, it didn't need much setting) in Karmic Koala. Everything works all right, except that it is extremely slow, when I try to use it in gimp. If I take the mouse, and choose a brush, I can draw very quickly, but if I want to do the same thing with the pen, I have to wait a lot. Has anyone experienced this before? If so, is there a quick fix for this problem?
Thanks,
v923z
PS: Here is the output of some diagnostics commands

anna@anna:/dev/input$ xsetwacom list
eraser     eraser
stylus     stylus

anna@anna:/dev/input$ dpkg -p wacom-tools  | grep Version
Version: 1:0.8.4.1-0ubuntu4

anna@anna:/dev/input$ dpkg -p gimp
Package: gimp                     
Priority: optional                
Section: graphics                 
Installed-Size: 12480             
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: i386                                               
Version: 2.6.7-1ubuntu1.1

---

### Post by james.king@4act.com on 2010-05-24
I have the same trouble with my Fujitsu ST5020D. It worked great when I was using Jaunty but when I upgraded to Karmic everything in Gimp slowed down considerably. 

I was thinking I would install an older version of Gimp (the version in the Jaunty repository) to see if it made a difference. Might be a while before I get to it though.

---

