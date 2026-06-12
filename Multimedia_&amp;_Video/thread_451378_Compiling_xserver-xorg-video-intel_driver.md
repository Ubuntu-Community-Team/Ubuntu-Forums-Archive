---
title: "Compiling xserver-xorg-video-intel driver?"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by capdog on 2007-05-22
Would it be possible to compile the latest version of the xserver-xorg-video-intel driver? I am trying to solve a problem and maybe upgrading from the one in the repository to the newest will help - I think there is a big difference, is there not?

Anyway, does anyone know how to install the bleeding edge version?

---

### Post by apos on 2008-01-25
It's an older thread, but I have the same problem.
I found [http://www.x.org/wiki/IntelGraphicsDriver?highlight=%28intel%29]("http://www.x.org/wiki/IntelGraphicsDriver?highlight=%28intel%29") as a starting point for this adventure. Due to real problems (see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/114331]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/114331")) with the next generation *xserver-xorg-video-intel* driver on my i830M chipset, I have to compile this driver.

Anybody done this on ubuntu?

Tips which *development packages* are required and how to handle the recompile of *agpgart* is VERY appreciated.

---

### Post by scumie on 2008-04-10
I've done this and was very simple IMHO. 
I'm using Ubuntu 8.04 Hardy Heron (Beta).

to get the deps simply do a :
# sudo apt-get build-dep xserver-xorg-video-intel build-essentials

then you need to get git-core to download

# sudo apt-get install git-core

and then get the latest version:

# mkdir source (or use a directory of your choice)
# git clone git://git.freedesktop.org/git/xorg/driver/xf86-video-intel
# cd xf86-video-intel

and to compile:
# ./autogen.sh --prefix=/opt/gfx-test --with-dri-drivers="i915 i965"
this is because I only want the drivers, not the rest as mesa.
# make
# sudo make install
(last one needs to be run as root/sudo)

The main reason I did it was the drivers for i965 incorrectly detect 2048 as max texture size, then compiz refused to run in dual monitor. i965 has a limit of 8192x8192 and I was hoping to modify the source and correct it. But the latest version in GIT already had the patch implemented so I just compiled and it worked.

The only caveat is that all applications are refusing to draw on larger planes that 2048x2048 anyway. Everything is functional, only a major cosmetic flaw on half of the desktop since nautilus is only drawing what it can (that is one screen and a half, my resolution is 1440x900 and that leaves only half of the second monitor's desktop - 1280x1024 only has 558 pixels) 

also nautilus gives the following warning which leads to a conclusion that the drivers are still giving wrong info somewhere.

** (nautilus:10016): WARNING **: Unable to add monitor: Not supported

everything is ok except for that half of screen. Screenshoot attached.

I hope this helps.

---

### Post by raggari on 2008-05-08
Thanks for instructions. Does this really install everything to /opt/gfx-test so that I can revert everything by removing /opt/gfx-test and apt-get install xserver-xorg-video-intel

---

