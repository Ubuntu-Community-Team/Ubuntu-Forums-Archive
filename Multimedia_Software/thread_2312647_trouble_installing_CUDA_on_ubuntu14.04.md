---
title: "trouble installing CUDA on ubuntu14.04"
date: 2016-02-06
forum: Multimedia Software
---

### Post by weiqiwang on 2016-02-06
[FONT=Calibri, sans-serif][COLOR=#000000]I am having following issue when I try to install CUDA6.5 on my laptop running ubuntu14.04:
[/COLOR][/FONT]
 The following packages have unmet dependencies: gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 libgl1-mesa-dri-lts-vivid : Conflicts: libgl1-mesa-dri
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

any leads? Thanks in advance.

---

### Post by Bucky Ball on 2016-02-06
*Thread moved to **Multimedia Software**.*

Welcome. Well, without more detail might be difficult. Install CUDA 6.5? Where from and how? Please provide links.

I will say those errors appear to be involved with Cheese. Do you have it installed? If not, install it and see if that makes any difference. Don't go hunting around for it like in Windows. Open Software Centre, type in 'Cheese', hit enter, when it pops up, install.

---

### Post by weiqiwang on 2016-02-06
It seems removing  [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) from software repo helps, now I am having trouble with fleeglut3-dev:

The following packages have unmet dependencies:
 freeglut3-dev : Depends: libgl1-mesa-dev or
                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
 gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Also libcheese-gtk23 and libcheese7 are seem to be installed,
:~/Downloads$ sudo apt-get install libcheese-gtk23
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcheese-gtk23 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Bucky Ball on 2016-02-06
Again, do you have Cheese installed?

---

