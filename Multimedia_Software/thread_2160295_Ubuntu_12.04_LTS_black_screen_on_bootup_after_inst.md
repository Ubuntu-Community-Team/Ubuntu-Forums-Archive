---
title: "Ubuntu 12.04 LTS black screen on bootup after installing libraries"
date: 2013-07-06
forum: Multimedia Software
---

### Post by thedemon13666 on 2013-07-06
Hi all,

I have to install some software for work, and in the guide I've been given, there is a list of prerequisite libraries that I need to install.  What I have found is that after installing the libraries, ubuntu boots to a black screen (although the back light is still on).  Here is the list of libraries/software I'm requested to install:


procmail, patch, make binutils, libx11-dev, libxpm-dev, libxft-dev, libxext-dev, gfortran,, libmysqlclient-dev, libfftw3-dev, graphviz-dev, python-dev, libxml2-dev, libssl-dev, libdrm-dev, libglu1-mesa-dev, libgl1-mesa-dev, libglew1.5-dev, libncurses5-dev, libxml2-dev, libmotif-dev, x11proto-core-dev, x11proto-print-dev, xorg-dev


After installing these libraries, I restart my laptop and I'm greeted by the black screen.  Oddly enough ctrl+alt+delete brings the purple ubuntu loading screen up and then the laptop restarts.  Obviously I can install the libraries one by one and restart until the laptop no longer boots, but it is going to take a bit of time to do, so I'm hoping someone may have some insight :)

I've successfuly done this on older versions of ubuntu so I know it is possible to get the software working on ubuntu.

Just a quick note, this is attempted on a fresh ubuntu 12.04 LTS install (after installing updates).

Laptop: Acer 5750g


Thanks guys!

---

### Post by thedemon13666 on 2013-07-06
Update:

I found that the X windows development libraries (xorg-dev) are causing the problem.  Installing all of the libraries except for xorg-dev don't cause any black screen problems.  
I'm hoping I can get by without xorg-dev but time will tell.

Anyone have any idea why xorg-dev is causing these problems on my acer 5750g.  I forgot to mention before that the 5750g uses nvidia optimus.  I have tested with and without bumblebee, but I still get the black screen.

---

### Post by Bucky Ball on 2013-07-06
*Thread moved to **Multimedia & Video**.*

I'll put it here for now. ***Installation & Upgrades*** intended for install and upgrade of the OS. ;)

---

