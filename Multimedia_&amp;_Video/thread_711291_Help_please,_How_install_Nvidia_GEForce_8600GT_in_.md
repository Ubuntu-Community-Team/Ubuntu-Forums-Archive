---
title: "Help please, How install Nvidia GEForce 8600GT in the Ubuntu V.7.10"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by jmosp on 2008-02-29
Dear Friends,

I have last time very dificulty to install the Driver of Nvidia Geforce 8600 GT in the ubuntu.
The Version of ubuntu that I am used is 7.10 Kernel 2.6.22-14.
I have search in many foruns that how install, so the every foruns have one manual basic that install.

when a try intall using any this manuals, occur


I am trying to install Driver of Nvidia Geforce 8600 GT in the ubuntu.
The Version of ubuntu that I am used is 7.10 Kernel 2.6.22-14.
However I am with many difficulties, would like to know if  they could help me in this task. I searched in the internet many  manual to help me in this installation and all are much seeming, to stop the server gdm, to execute driver of installation etc. 
But when I try to install it occurs the errors below. 

[COLOR="Red"]sing: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
[/COLOR]

Now I do not know if the version of the Linux which I am using is not compatible or Kernel,  if I am committing some error. 

I formatted the machine installed linux again, and lowered all the possible updates for this version and nothing he functioned, being thus would like an aid. could you place a manual step by step of as to install it will be had.

Thanks for all, and
Sorry for my english that not very good.

---

### Post by ubuntu-freak on 2008-02-29
Did you actually install Ubuntu okay? If not, you need to use the alternative ISO, and not the Live CD ISO. Then you can install your 8600 drivers with [Envy](http://albertomilone.com/nvidia_scripts1.html). 
 
Nathan

---

