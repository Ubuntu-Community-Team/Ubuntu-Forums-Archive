---
title: "nw802 webcam driver install problem"
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by ephman on 2005-12-25
hi,

i have a dark ring usb logitech webcam that needs to use the nw802 driver, and i'm having an issue with installing it. any help would be appreciated.

here are the instructions:
cvs -dserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802 login
cvs -z3 -dserver:anonymous@cvs.nw802.sourceforge.net:/cvsroot/nw802
co nw802-2.4
cd nw802-2.4
cp Makefile.26 Makefile
patch -p0 < patch-2.6
make clean
make

when i get to "co nw802-2.4" command i get: "bash: co: command not found"

any help would be awesome i'd love to get this camera going thanks...

thanks for the bandwidth,
ephman

---

### Post by dancho on 2006-12-07
Hey! You posted a long time ago and nobody answered.  Here's the deal. The directions say "co", but it should be "cvs co" on every line where it's co.  The program used is not "co" but "cvs".

---

