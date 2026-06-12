---
title: "trouble with nvidia driver (building NVIDIA kernel module)"
date: 2009-01-07
forum: Multimedia Software
---

### Post by lamikins on 2009-01-07
Hallo,
I'm having trouble installing an nvidia driver! 'Tis getting a little ridiculous.  Also - a preemptive apology for this godawfully long post...

This is what I've been doing:
I was having some trouble with restricted nvidia drivers (every time i enabled them, resolution went bonkers and text fonts were wacky).  I had tried Envy, Synaptic, System --> Hardware Drivers, aptitude...  all with essentially the same effect.  So...

I stripped my newly updated Xubuntu 8.10 Intrepid system of everything nvidia related and started with a clean slate. 

I downloaded the correct driver for my GeForce 4 MX series:

(lamikins@russia:/var/log$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

So correct driver was "NVIDIA-Linux-x86-96.43.07-pkg1.run", which I saved to my home directory.)


I added "nvidia" to /etc/modules and added DISABLED_MODULES="nv" to the restricted list in /etc/default/linux-restricted-modules-common.

Then I turned off X (sudo /etc/init.d/gdm stop) and made the NVIDIA installer executable (sudo chmod a+x ./NVIDIA*.run) then ran the installer (sudo ./NVIDIA*.run).  

(I have also tried this with simply "sh NVIDIA-Linux-x86-96.43.07-pkg1.run" to the same effect)

But (and here's the kicker) the installer can't find a precompiled kernel interface and attempts to build one.  I get:

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
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
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

And then get told:

ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I've read this README, but I'm still stumped on how to proceed.  I've ensured my kernel (and headers) is up to date:

lamikins@russia:~$ sudo apt-get install linux-headers-2.6.27-9-generic
[sudo] password for lamikins: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.27-9-generic is already the newest version.
linux-headers-2.6.27-9-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I can't see why the build is failing :(  (NB build-essential package is installed)

I'm really stuck, any help would be greatly appreciated and once again I apologise for the length of this ramble.

---

### Post by ricardo_78 on 2009-01-08
I am experiencing exactly the same problem. [See Thread ]("http://ubuntuforums.org/showthread.php?t=1033536") I have not tried this yet.

---

### Post by lamikins on 2009-01-08
Thanks for the redirect, but sadly it didn't solve my problem :(  Still stumped (double :().

---

