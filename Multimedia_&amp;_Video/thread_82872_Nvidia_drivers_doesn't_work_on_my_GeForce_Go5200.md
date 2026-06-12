---
title: "Nvidia drivers doesn't work on my GeForce Go5200"
date: 2005-10-27
forum: Multimedia &amp; Video
---

### Post by stefann on 2005-10-27
I'm having trouble to get the nvidia drivers to work on my laptop. I've done apt-get install on nvidia-glx, linux-restricted-modules-$(uname -r) and nvidia-settings. I also removed dri and glcore from xorg.conf and added glx and changed nv to nvidia.

Even so, when i restart X i can just barely see the nvidia-logo flash by and then the screen goes black.

In a desperate attempt to make it work i tried to compile the later version of the drivers, but then it complained about this while building the drivers:
> 
  '--ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.

       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.


Even though i've actually apt-get installed the correct things following the guide on these forums.

The reason I'm going through all this trouble is that i want to use tv-out on my gfx-card.

---

### Post by stefann on 2005-10-28
Noone who has a solution to this problem? Or who knows where to search? I've been googling as crazy.

---

### Post by stefann on 2005-10-28
Solved! I managed to compile the driver (7667?) from source, and then it worked!

---

### Post by james7824 on 2006-07-17
what does that mean exactly? im new to all this so if you could be as specific as you could i would greatly appreciate it.

---

