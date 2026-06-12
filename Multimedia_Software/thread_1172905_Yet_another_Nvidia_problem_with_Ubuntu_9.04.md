---
title: "Yet another Nvidia problem with Ubuntu 9.04"
date: 2009-05-29
forum: Multimedia Software
---

### Post by black plague on 2009-05-29
Hello all!  I'm yet another Linux noob, been using Ubuntu 8.04 for about six months now and decided to go through the upgrades and start using 9.04.

My computer is an HP Pavilion dv6000 laptop with an amd64 processor and an NVidia GeForce 7150M/NForce 630M card.  I had everything working fine in 8.04, then of course upon upgrade my display goes back to the ugly, old low-res 800 x 600.  

I tried using both of the NVidia drivers provided in the Hardware Drivers menu, but while both would appear to activate, a reboot would give me an error and put me right back into low-res mode, so bad that it usually required going into recovery mode and using xfix.

So I tried doing the HowTo located at [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) and now the drivers have been deleted from the Hardware Drivers menu.

So I'm trying to do a manual install of the driver (using NVIDIA-Linux-x86_64-180.51-pkg2.run), it craps out on me, and this is the error log I receive.

> [FONT=Courier New]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri May 29 01:55:07 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
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
-> Installing NVIDIA driver version 180.51.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.2) does not exactly match the
   current compiler (gcc 4.3).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
[/FONT]

So I checked "gcc -v" and "cat /proc/version" and the log is correct...my compiler is a version above the one that compiled my kernel.  I have build-essentials installed already, I've tried updating everything with apt-get and aptitude both...but to no avail.

I've pulled my hair out, searching every possible answer with no luck.  Normally, I can find a previous post here where someone's had the same problem and had it solved and learn from that.  But not this time, unfortunately.  If all else fails, I can just reinstall 8.04...but I really don't want to have to back up and reconfigure all my stuff, plus I like that the Atheros drivers finally work well in 9.04 and I don't have to use madwifi anymore.

I am still a noob at all this, so if anyone has answer, please give it to me step-by-step and with all the necessary terminal commands.

Thanks in advance!

---

### Post by black plague on 2009-05-29
bump

---

### Post by MedellinManDem on 2009-05-30
> **black plague said:**
> bump

I have a similar problem. 

Cannot believe no one has bothered to help.

---

### Post by Arup on 2009-05-30
Try sudo apt-get install build-essential uname -r 

Also make sure nvidia development kernel is installed. Check this thread as well.

[http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951](http://www.nvnews.net/vbulletin/showthread.php?p=2014951&posted=1#post2014951)

---

