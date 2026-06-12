---
title: "nVidia driver installation holdup?"
date: 2005-12-15
forum: Multimedia &amp; Video
---

### Post by handy on 2005-12-15
Hi,
I've started my way down the path of nVidia driver installation, to get the best out of my 6800 GT card.  I am following "Artificial Intelligence's" good looking instructions from here  [http://doc.gwos.org/index.php/Install_Nvidia_other_drivers](http://doc.gwos.org/index.php/Install_Nvidia_other_drivers)
I'm stopped with an error when I run the "sudo sh nvidia.run" command.  (I've renamed the driver to something more managable, if you were wondering.)  

Pertinant sections of the error follows:

===============================================================
The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel. 
The compiler used to compile the kernel was gcc 3.4; the current compiler is gcc 4.0.

If you know what you are doing and want to ignore the gcc version check, select "No" to continue installation.  Otherwise, select "Yes" to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel, and restart installation.
===============================================================

So, my query is this, where do I find the file to set the CC environment variable to "gcc 3.4"?

Thanks for your time.

handy

---

### Post by kg4gyt on 2005-12-15
First make sure you have gcc-3.4 installed
```
sudo apt-get install gcc-3.4
```
Then export CC.
```
export CC=gcc-3.4
```
Note that there is no sudo on the export.

I had several problems when I installed the driver, I hadn to use multiple switches that I could only find in the advanced help section for the nVidia installer, but everything ended up working out.   You may want to disable usplash in your /boot/grub/menu.lst file becuase it seems that if you don't then the system will freeze and crash whenever you switch between terminals or log off, restart X etc.

---

### Post by handy on 2005-12-15
Thanks for the excellent help kg4gyt :-)

 I'll get to it tomorrow night, time for bed now.

Cheers,

handy

---

