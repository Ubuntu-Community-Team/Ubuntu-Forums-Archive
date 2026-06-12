---
title: "Problems installing new Nvidia driver"
date: 2005-12-15
forum: Multimedia &amp; Video
---

### Post by bogoliubov on 2005-12-15
Hello. I just downloaded the newest nvidia drivers from the Nvidia homepage.
I quit X11 by Ctrl Alt F1, logged in as root and did "killall gdm".

Then I tried to install the new driver. But the installer couln't finish and I couldn't understand why either...   Any help is greatly appreciated!

I attach the log file from the installation...
----------------------------------------------------------------------------------------------------

$ cat /var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Dec 15 23:09:44 2005

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
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
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

### Post by stuporglue on 2005-12-15
> -> Performing CC test with CC="cc".
...
./usr/src/nv/conftest.sh: line 19: cc: command not found


You need to install GCC. You do this by installing "build-essential".

---

### Post by bogoliubov on 2005-12-15
Thanks for the tip! Do I need to remove the "nvidia-glx" package?

---

### Post by MartinG on 2005-12-15
You may also need gcc 3.4 (not part of build-essential), and you will need kernel headers.  You may also find you need to remove linux-restricted-modules.  See the two threads listed below for some people's previous experiences.

[http://www.ubuntuforums.org/showthread.php?t=100859](http://www.ubuntuforums.org/showthread.php?t=100859)
[http://www.ubuntuforums.org/showthread.php?t=103030](http://www.ubuntuforums.org/showthread.php?t=103030)

---

### Post by bogoliubov on 2005-12-15
[QUOTE=MartinG]You may also need gcc 3.4 (not part of build-essential), and you will need kernel headers.  You may also find you need to remove linux-restricted-modules.  See the two threads listed below for some people's previous experiences.

[http://www.ubuntuforums.org/showthread.php?t=100859](http://www.ubuntuforums.org/showthread.php?t=100859)
[http://www.ubuntuforums.org/showthread.php?t=103030](http://www.ubuntuforums.org/showthread.php?t=103030)[/QUOTE]


Thanks. I'll give it a try! I don't know what I'd do without all help I get at this forum... :)

---

### Post by bogoliubov on 2005-12-15
...But somehow I f*cked up, because I forgot to install the kernel-headers.
The driver did not install correctly. Now X won't start and I don't know what to do (I'm writing this on my laptop...).

If I try apt-get install kernel-headers it says that I don't have any "installation candidate" (directly translated to english). The same goes for aptitude...

So, what can I do?

---

### Post by harty83 on 2005-12-15
You can try to uninstall the drivers by typing "sudo sh /location/to/NVIDIA-Linux-x86-1.0-VERSION-pgk1.run --uninstall"  

Edit /etc/X11/xorg.conf and replace "nvidia" with "nv" and you will then be able to get back into your system and work from there.

---

### Post by bogoliubov on 2005-12-15
[QUOTE=harty83]You can try to uninstall the drivers by typing "sudo sh /location/to/NVIDIA-Linux-x86-1.0-VERSION-pgk1.run --uninstall"  

Edit /etc/X11/xorg.conf and replace "nvidia" with "nv" and you will then be able to get back into your system and work from there.[/QUOTE]

I didn't need to uninstall, since the installation failed. But I should have been able to figure out the xorg.conf part myself..., well I can only say that it's late over here...  :)

---

### Post by handy on 2005-12-15
I had your problem early this morning, stuffed up my repository routine to boot, my fault, I'm still too new at linux.  
Anyway I've reinstalled & configured things back to where they were, doesn't take too long at this stage thankfully.

I now have the nVidia drivers installed, without having to shutdown x or anything, just 1 reboot at the end  :-)

Here's a link to the simplest howto I've seen for the nVidia gfx driver install:

[http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)

I just used it & it worked beautifully for me except the menu entry doesn't call nvidia-settings,  I'll sort that out soon enough.

See Glxgears fps rate below, before the driver install I was on about 20fps!!

handy@BirdFish:~$ glxgears
63167 frames in 5.0 seconds = 12633.356 FPS
65566 frames in 5.0 seconds = 13113.006 FPS
61099 frames in 5.0 seconds = 12219.640 FPS
65319 frames in 5.0 seconds = 13063.763 FPS
65395 frames in 5.0 seconds = 13078.804 FPS
65363 frames in 5.0 seconds = 13072.581 FPS
65374 frames in 5.0 seconds = 13074.735 FPS
64333 frames in 5.0 seconds = 12866.407 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
handy@BirdFish:~$

I hope that this has helped someone in here  :-)

handy

---

### Post by bogoliubov on 2005-12-16
Thank you; but I was trying to get the latest nvidia driver. The one you have in the repository is older. Well, sooner or later the new driver will appear in the repository and the it'll be easy to update it...

---

### Post by codejunkie on 2005-12-16
[QUOTE=bogoliubov]...But somehow I f*cked up, because I forgot to install the kernel-headers.
The driver did not install correctly. Now X won't start and I don't know what to do (I'm writing this on my laptop...).

If I try apt-get install kernel-headers it says that I don't have any "installation candidate" (directly translated to english). The same goes for aptitude...

So, what can I do?[/QUOTE]
the reason your getting the "installation candidate" error when trying to install the kernel headers package is in ubuntu the kernel headers package is called linux-headers-yourkernelversion the easiest way to install them is to use this command 
```
sudo apt-get install linux-headers-`uname -r`
```
hope this helps.
also this guide will give you a detailed walk through on how to install the drivers 
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

