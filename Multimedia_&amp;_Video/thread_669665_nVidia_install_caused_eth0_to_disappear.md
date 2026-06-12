---
title: "nVidia install caused eth0 to disappear"
date: 2008-01-16
forum: Multimedia &amp; Video
---

### Post by metaphorz on 2008-01-16
yesterday, when I tried to install the nvidia driver (on a 
Dell Vostro 400 with an Nvidia 8600 GTS), somehow,
I managed to remove the "wired connection" (eth0)
during the installation. 

I have a 7.10 server with the 7.10 ubuntu-desktop installed
on top of it.

I since rebuilt the system (7.10) since it is
brand new, but here was the original procedure I used:

1. Synaptic -> nvidia-glx (install)
2. sudo nvidia-glx-config enable

I had backed up my /etc/X11/xorg.conf file first but restoring
this file did not bring eth0 back.

uname -a 

shows the "server" kernel. Is the generic restricted modules
still applicable? After the rebuild, I went into System-Admin to
see what Restricted Drivers Manager would do. It said:

 "You need to install the package

  linux-restricted-modules-2.6.22-14-server for this program to work"

but a sudo apt-get install linux-restricted-modules-2.6.22-14-server"

results in being not found in the online repository

---

