---
title: "Nvidia &gt; API Mismatch after reboot"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by chickan on 2007-04-21
So after installing the nvidia 9755 drivers, everything works great, glxgears/beryl both work well.  However, when I reboot X fails to start, and complains about an API mismatch saying "the Nvidia kernel module has the version 1-0-7184 but this X module has the version 1.0-9755".

Going in and reinstalling the NV drivers solves the problem, but only until I reboot, then it is back.  I found this thread: [http://ubuntuforums.org/showthread.php?t=415854](http://ubuntuforums.org/showthread.php?t=415854) but none of the solutions in there work.  Following this thread: [http://ubuntuforums.org/showthread.php?t=409009&page=2](http://ubuntuforums.org/showthread.php?t=409009&page=2) and trying to install nvidia-glx-new, I get the following output: 

chickan@chickan-desktop:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-bin libgnome32 gnome-libs-data libnspr4-0d libcpufreq0 libart2
  libgnorbagtk0 libgnomeprint-data libgnomeui32 libxml1 libdb3 libgdk-pixbuf2
  imlib-base liborbit0 gdk-imlib11 libpq4 libgnomesupport0 libgnomeprint15
  libnss3-0d dpatch libgnorba27 libgnomeprint-bin
Use 'apt-get autoremove' to remove them.
Suggested packages:
  nvidia-new-kernel-source
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4833kB of archives.
After unpacking 14.7MB of additional disk space will be used.
(Reading database ... 121092 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I think the problem is, I originally had an ATI card in here, but now that I have switched to an Nvidia card, the two sets of drivers are clashing.  I've uninstalled all the fglrx drivers from within synaptic, but I still get this conflict.  I tried "sudo apt-get remove xorg-driver-fglrx" and exits saying nothing to remove.

Any thoughts?  The new video card is a PNY 7900gt, old is X800gto.

---

### Post by chickan on 2007-04-23
friendly bump ?

---

