---
title: "NVIDIA drivers install problem"
date: 2006-03-14
forum: Multimedia &amp; Video
---

### Post by wolf_3d on 2006-03-14
I need to install the nvidia display drivers so i can play Enemy Territory. I have downloaded the drivers from Nvidia's website and have gone into root and executed the install file. I get this error message:

[CENTER]ERROR: Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.

                                       OK[/CENTER]

Binutils are a set of binary tools. Where can i get them from? I have been looking around and can't seem to find them.

---

### Post by predaeus on 2006-03-14
try

[INDENT]sudo apt-get install binutils[/INDENT]

if it still fails, try

[INDENT]sudo apt-get install build-essential[/INDENT]

EDIT: you can leave out the 'sudo' when root

---

### Post by wolf_3d on 2006-03-14
thank you predaeus that worked fine. I killed X server and It allows me past that stage and now i am stuck again. It comes up with an error about no precompiled kernel. Here is the NVIDIA installer log file:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Mar 14 18:13:02 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC test with CC="cc".
-> gcc-version-check failed:
   
   ./usr/src/nv/conftest.sh: line 19: cc: command not found
   
   Could not compile gcc-version-check.c.  Please be sure you have your distrib
   ution's libc development package installed and that 'cc' is a valid C compil
   er name.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Adrian_b on 2006-03-14
It's
```

CC=gcc-3.4
export CC

```
And that it doesn't find a precompiled kernel is normal..

Take a look at Method 2 of [http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
It's a terrific guide!

---

### Post by wolf_3d on 2006-03-15
Problem solved. That was the guide i was looking for when i stumbled across it the other day. Must have forgotten to bookmark. Thx everyone.:-D

---

