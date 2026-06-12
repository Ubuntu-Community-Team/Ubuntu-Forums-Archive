---
title: "getting glx working"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by Mazehero55 on 2007-01-10
I'm having trouble getting my graphics working, I believe I have a nvidia geforce 2 mx 400 or something like that; I know it's at least a geforce2. I think that means I need legacy glx right?

But when I install nvidia-glx-legacy it crashes my xserver. I don't really know what to do to get it working to get glx working.

I also went and put in glxinfo | grep direct and this came out

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Any help would be great really. 
thank you so much

---

### Post by scrooge_74 on 2007-01-10
did you follow the instructions? 

[http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)

---

### Post by RaZoR-x11 on 2007-01-10
Hey there,

Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This is a admazing script made by tseliot it will solve all your prob's.

---

### Post by Mazehero55 on 2007-01-10
Okay I have downloaded envy. I ran it and it downloaded alot of stuf. But at the end there was an error. I'm not sure what to do.

here's the log it came out with
```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jan 10 19:10:44 2007

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : false
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
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
  X install prefix        : /usr/lib/xorg/modules
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.15-26-386
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.15-26-386' as
   specified by the '--kernel-source-path' commandline option.
ERROR: The kernel source path '/usr/src/linux-headers-2.6.15-26-386' does not
       exist.  Please make sure you have installed the kernel source files for
       your kernel and that they are properly configured; on Red Hat Linux
       systems, for example, be sure you have the 'kernel-source' or
       'kernel-devel' RPM installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

I think it might have something to do with the fact that I think I have an AMD processor and I think my kernal is an intel one. But i'm not sure.

thanks

---

### Post by useResa on 2007-01-13
I just came across your post and I notice in the log that you are posting the following:
> ERROR: The kernel source path '/usr/src/linux-headers-2.6.15-26-386' does not
       exist.  Please make sure you have installed the kernel source files for
       your kernel and that they are properly configured

Maybe an obvious question but just to be sure, have you installed the linux headers?

---

### Post by scrooge_74 on 2007-01-13
> **useResa said:**
> I just came across your post and I notice in the log that you are posting the following:


Maybe an obvious question but just to be sure, have you installed the linux headers?

Your are right, I didnt have time yesterday  to read the entire log, but he do needs to install the headers

---

