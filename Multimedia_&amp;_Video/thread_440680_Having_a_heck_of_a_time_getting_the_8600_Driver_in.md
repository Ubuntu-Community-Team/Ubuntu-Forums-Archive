---
title: "Having a heck of a time getting the 8600 Driver installed"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by WickedAwsome on 2007-05-11
well...as it is, the "nv" is the default driver being used and I am unable to get any others installed.  I  installed the one that automatix, and some tutorials for beryl recomended (nvidia-glx) and neither worked. 

 I found the beta drivers for my 8600 from the NVIDIA website, but I am unable to install them

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri May 11 21:03:54 2007

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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

this is the error during the installation.  I dont have the libc header files? I checked synaptics manager and it said I had the libc6 installed, so I figured that was it and I couldnt figure it out.  also the no precompiled kernel interface?  Not sure...it would be nice to get this going so I can get out of "0ld-People" resolution and have a cube again.  

Thanks!

---

### Post by RomeReactor on 2007-05-11
> ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's **libc development package**.

Hi. You need to install **libc6-dev**; that's the package that provides the headers.

---

### Post by WickedAwsome on 2007-05-12
well...that got the driver installed...however now I have no video at all... when I start GDM from recovery mode it is just black, and in normal mode it has no video at all.  I went into the xorg.conf file and switched back to the nv driver and it still didn't work, so I have effectively made it worse.

I got the driver it recomened on the nvidia page I think...the only thing i wasnt sure about was the AMD64/EM64T or IA64... a c2d is EM64T right?


Any suggestions? 

Thanks again,
Gary

---

### Post by LordNikon9x on 2007-05-12
Do you have nvidia-glx installed? if so, then on every boot the old driver gets loaded. I have to manually remove nvidia module, then load it again, this time it loads the correct one, and restart kdm.

I have other problems with nvidia beta driver, for example: programs under wine work only if I place window to top left corner of the screen, some things do not want to start at all with wine:
```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  72 (X_PutImage)
  Serial number of failed request:  82
  Current serial number in output stream:  94

```
or some other similar errors.

---

### Post by RomeReactor on 2007-05-12
> **WickedAwsome said:**
> a c2d is EM64T right?

Technically yes, though that refers to the architecture of the OS rather than the processor: If you installed Ubuntu 32-bit, then you need the [IA32]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html") drivers. Did you install drivers from Synaptic *and* the ones downloaded from the nVidia site? If you only have installed the drivers once (using either method) try doing this from the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and 

```
startx
```

to see if that brings you to your desktop.

---

