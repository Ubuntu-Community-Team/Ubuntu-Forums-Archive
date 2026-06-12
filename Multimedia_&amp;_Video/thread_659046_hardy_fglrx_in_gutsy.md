---
title: "hardy fglrx in gutsy"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by puccaso on 2008-01-05
ok - i have an ati x1400 card, one of those tripe handlers that doesnt work with the normal old fglrx stuff. so i need to use the new ones..
but - whenever i use the fglrx binary drivers from ati - my suspend never works.
so i have to switch between two xorg.confs. one with vesa - so i can suspend and one with fglrx so i can play games etc.. 

now - somehow - the fglrx in hardy - it doesnt have this problem.
i have opengl and i can suspend! this is amazing. now my question is
how do i get the xorg-driver-fglrx package installed on gutsy?

i cant just use the 7.11 drivers from ati - and do it the buildpkg way - it doesnt allow me to suspend that way - iv tried it.

any ideas?

---

### Post by puccaso on 2008-01-05
ok
im trying it myself
i added the hardy reps to my apt sources
and im trying to install it

this is what it says

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
   libc6 (2.7-5ubuntu2)
   libc6-i686 (2.7-5ubuntu2)
Suggested packages:
   glibc-doc (2.7-5ubuntu2)
The following NEW packages will be installed
   xorg-driver-fglrx (7.1.0-7-11+2.6.24.3-2.9)
The following packages will be upgraded:
   libc6 (2.6.1-1ubuntu10 => 2.7-5ubuntu2)
   libc6-i686 (2.6.1-1ubuntu10 => 2.7-5ubuntu2)
2 upgraded, 1 newly installed, 0 to remove and 738 not upgraded.
Need to get 18.3MB of archives.
After unpacking 33.4MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

what should i do?
will it mess anything up?

---

### Post by acoustibop on 2008-01-05
The fglrx 7.12 driver has been out for awhile now, puccaso.  Have you tried the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") method?  It's always worked well for me on a number of fglrx installations.

---

### Post by puccaso on 2008-01-05
iv done all this stuff before
you get opengl
but you cannot suspend
and nothing iv tried works.
with the xorg-driver-fglrx
it suspends without having to play with anything

---

