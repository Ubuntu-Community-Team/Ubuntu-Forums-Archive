---
title: "Nvidia GeForce 6150B+nForce 430 drivers"
date: 2009-11-16
forum: Multimedia Software
---

### Post by jeditalian on 2009-11-16
using ubuntu 9.10 64 bit.
i have a foxconn winfast 6150bk8mc with nVidia GeForce 6150B + nForce 430 onboard. my sound works, but my video looks strange and my available resolutions are 800x600 and below. im not sure how to get drivers for ubuntu. i downloaded some linux drivers but they were a .run file or something so i couldnt do anything with them. i'm guessing everything else has a decent driver, since i'm online and i have sound, and my usb pci card works. my synaptic package handler has been having issues since i ran this script this other thread gave me.. so, should i use synaptic, or ubuntu software center, or how should i get some decent drivers?
EDIT: ok. i found how to run these .run files, but how do i run as root? 
 ERROR: nvidia-installer must be run as root

heres the log after i change directory, then sudo ./ thename.run 
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Nov 16 01:09:49 2009
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
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1278'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by jeditalian on 2009-11-16
k nevermnd. i will probably figure it out before this gets a reply.

---

### Post by jeditalian on 2009-11-16
okay. new question. how do i delete this thread?

---

### Post by Lvcoyote on 2009-11-16
System/administration/hardware drivers.... do you get an option to install proprietary nvidia drivers?

---

### Post by jeditalian on 2009-11-19
i wish i would have posted how i solved this the first time. no. when i click hardware drivers it just says No proprietary drivers are in use on this system, but i havent downloaded anything yet as i just reinstalled ubuntu to get out of the problem of 640x480 @50hz max with clean text, which got me back here with wavy text and 800x600@ 60 hz max res. with pixelated wavy text. My monitor says: Part 4522 131 59342
Serial 01054 software P270P12B Temp Max 60C Act 51C Backlight BLS 199 BLL 81
Timing V: 55.9Hz H: 35.0kHz, SVGA,  H/V-Sync, Vsync: Pos, Hsync: Pos . It's a PHILIPS and i think it came from a hospital before i bought it, and searching the Part# 4522 131 59342 only tells me that its the monitor from an old MRI machine. no drivers. 
I've had my display working nicely with ubuntu before. i just ran the monitors autoadjust and the text is alot cleaner but still wobbly like an animated gif. 
No proprietary drivers are in use on this system. what should i download to support my Nvidia?
update: installing 114 updates now. will report back whether or not they help.
I think i need to find the .run file i mentioned on the first post. I believe i did a gksudo nautilus or something to run it as root. idk though. if i install all that nvidia stuff, my video jumps 


                                                  about this far of a difference when i click inside of the display settings. i think that .run allowed me to access higher resolution and refresh rates, but it still had the issue of jumping everytime i clicked (only in the display settings manager) and not being able to save configuration to xorg.conf.

---

### Post by jeditalian on 2009-11-19
"System/administration/hardware drivers.... do you get an option to install proprietary nvidia drivers?"
 now i have the option. it says driver ver. 185 is recommended. so ima try it. *downloading and installing driver...* now ineed to reboot to use the driver so i'll be back to say how it works.

---

### Post by jeditalian on 2009-11-19
ok it works like this its just hte nvidia xserver cant save the configuration to the xorg.conf 
Failed to parse existing X config file '/etc/X11/xorg.conf'! click ok and the xserver window closes. 
all that is in the xorg.conf is: 
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by jeditalian on 2009-11-20
i guess if this happens to you, run Update manager, if that fails, backup your goodies and do a nice clean install, then try update manager.

---

### Post by jeditalian on 2009-11-21
actually im wrong(big surprise!) do the system-administration-hardware drivers thing after doing the update manager thing

---

### Post by gordong11 on 2009-11-21
Do a clean install, save your files first. Your mistake was downloading those drivers, it corrupted your x-server and will never be the same.

IT doesn't matter which is done first, update manager or Hardware Drivers, just remember to use Hardware Drivers utility. Reboot, and go back to harware drivers and make sure light is green and activated,

---

