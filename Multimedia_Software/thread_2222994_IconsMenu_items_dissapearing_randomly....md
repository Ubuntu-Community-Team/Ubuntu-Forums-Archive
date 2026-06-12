---
title: "Icons/Menu items dissapearing randomly..."
date: 2014-05-09
forum: Multimedia Software
---

### Post by stretch4 on 2014-05-09
I have a fresh install of Xubuntu.  I'm using the Xfce desktop.  Icons and menu items are dissapearing, seemingly at random.  They are still there, they are just not visible. If I cause them to move (scrolling) or roll the pointer over them, sometimes they will reappear/disappear. If I click on them, they function normally.  This happens in menus, on the desktop, and even the formatting controls in this forum are just empty spaces where they should be. Does anybody know how I can start troubleshooting this? I've got some screenshots so that you can see what I'm talking about...

[IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2002%3A48%3A41%20PM.png[/IMG]  [IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2003%3A09%3A34%20PM.png[/IMG][IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2003%3A12%3A04%20PM.png[/IMG] [IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2003%3A21%3A26%20PM.png[/IMG] [IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2003%3A22%3A07%20PM.png[/IMG] [IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2003%3A30%3A36%20PM.png[/IMG] [IMG]https://dl.dropboxusercontent.com/u/94399016/Icon%20Glitch/Screenshot%20-%2005082014%20-%2009%3A57%3A33%20PM.png[/IMG]

---

### Post by Toz on 2014-05-09
Hello and welcome to the forums.

Which appearance theme are you using? (Settings Manager >> Appearance >> Style tab)? Have you tried changing the theme? Does it make a difference?
Have you made any manual edits to any of your gtk configuration files (~/.gtkrc-2.0, /etc/gtk-2.0/gtkrc, ~/.config/gtk-3.0/*, /etc/gtk-3.0/*)?

---

### Post by stretch4 on 2014-05-09
> **Toz said:**
> Which appearance theme are you using? (Settings Manager >> Appearance >> Style tab)?
I am using Numix.

> **Toz said:**
> Have you tried changing the theme? Does it make a difference?
Yes, I have tried.  Same problem regardless of theme selection.

> **Toz said:**
> Have you made any manual edits to any of your gtk configuration files (~/.gtkrc-2.0, /etc/gtk-2.0/gtkrc, ~/.config/gtk-3.0/*, /etc/gtk-3.0/*)?
No.

---

### Post by Toz on 2014-05-10
Which video card do you have and which driver are you using?
```
lspci -k | grep -iA2 VGA
```

Do you have composting enabled (Settings Manager >> Window Manager Tweaks >> Compositor? Does it help if you disable it?

Does reinstalling librsvg2 and librsvg2-common help:
```
sudo apt-get install --reinstall librsvg2 librsvg2-common
```

---

### Post by stretch4 on 2014-05-10
> **Toz said:**
> Which video card do you have and which driver are you using?
```
lspci -k | grep -iA2 VGA
```
```
$ lspci -k | grep -iA2 VGA
02:00.0 VGA compatible controller: NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MSI GeForce4 MX T8X with AGP8X
    Kernel driver in use: nouveau
```

> **Toz said:**
> Do you have composting enabled (Settings Manager >> Window Manager Tweaks >> Compositor? Does it help if you disable it?
It is disabled.
If I enable it, my CPU maxes out and my systems slows to a crawl. (AMD Athlon XP is pretty weak.)

> **Toz said:**
> Does reinstalling librsvg2 and librsvg2-common help:
```
sudo apt-get install --reinstall librsvg2 librsvg2-common
```
```
$ sudo apt-get install --reinstall librsvg2 librsvg2-common
[sudo] password for stretch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package librsvg2
```

---

### Post by Toz on 2014-05-10
> **stretch4 said:**
> ```
$ lspci -k | grep -iA2 VGA
02:00.0 VGA compatible controller: NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MSI GeForce4 MX T8X with AGP8X
    Kernel driver in use: nouveau
```
Have you tried with the proprietary nvidia driver?

> ```
$ sudo apt-get install --reinstall librsvg2 librsvg2-common
[sudo] password for stretch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package librsvg2
```
Sorry, my bad. It should be:
```
sudo apt-get install --reinstall librsvg2-2
```

---

### Post by stretch4 on 2014-05-10
> **Toz said:**
> Sorry, my bad. It should be:
```
sudo apt-get install --reinstall librsvg2-2
```

Yeah, I thought that might be what you meant, so I re-installed librsvg2-2.
No change.

> **Toz said:**
> Have you tried with the proprietary nvidia driver? 
I'll see if I can hunt it down.  When I was installing Windows XP, it was a real bitch to find.

---

### Post by stretch4 on 2014-05-11
Well, I found the driver.  But, I'm having problems installing it.  It says it can't find the kernel source files or something... here's the log file.  It's got the error messages at the bottom.
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat May 10 20:57:39 2014
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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 96.43.07.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: The kernel header file
       '/lib/modules/3.13.0-24-generic/build/include/linux/version.h' does not
       exist.  The most likely reason for this is that the kernel source files
       in '/lib/modules/3.13.0-24-generic/build' have not been configured.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Toz on 2014-05-11
Go to Settings Manager -> Additional Drivers. It should be listed there with the option to enable it. It is much easier to use this method to enable the proprietary drivers.

---

### Post by stretch4 on 2014-05-12
I went ahead and clean-installed Lubuntu.  It seems to run a bit faster.  However, I'm still experienceing the same graphics problem.  I've repeated all of the above steps and so far all the results have been the same.

> **Toz said:**
> Go to Settings Manager -> Additional Drivers. It should be listed there with the option to enable it. It is much easier to use this method to enable the proprietary drivers.

It says "No additional drivers available."

---

### Post by stretch4 on 2014-05-12
I did a fresh install of Lubuntu. Same problem. I repeated all the steps we've taken, no success.

---

### Post by ntu on 2014-05-31
Stretch4, I have the same problem with Both Ubuntu and Lubuntu 14.04 and have given up on them as a result. Sorry to not provide any help with this post.

---

### Post by Gerd_Wilhelm on 2014-06-13
Hi.
I have the same problem and here is what i found out:

1) the nouveau driver produces the glitches (dispearing icons, somtimes white on white font and so on)
2) The last driver from Nvidia which supports nv18 does not support Kenrel 3.x
3) The Vesa Driver ist slow an does not support higher Screen resolutions

What to do? 

You can disable 2d/3d acceleration in the nouveau driver. It will be as slow as Vesa, but the glitches are gone and you can use higher resolutions. Here are two ways to do this:
[U]
[SIZE=3]First Solution: easy way to turn of acceleration:[/SIZE][/U]

1) Edit /etc/default/grub and change the line GRUB_CMDLINE_LINUX_DEFAULT so that it reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nouveau.noaccel=1"
```
2) run ```
sudo update-grub
```
3) reboot

Now the glitches are gone, but your graphic is slow. Might be OK vor office use, but video playback or desptops effects are unusable slow

[SIZE=3]_Second Solution: add a second bootmenuentry to be able to choose at boot time wether to turn off acceleration or not:_[/SIZE]

I have adjusted grub, so that i can decide at boot time wether i want acceleration (for example for video playback), or not. unfortunatly the machine i done this for is not here at the moment, so can't give exact code, bit in general this works like that.

1) Make sure joe undo the changes from solution a)
2) edit /etc/grub.d/10_linux 
2a) in about line 314 find a section like that:```

linux_entry "${OS}" "${version}" simple \
    "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
```
2b) Duplicate that Section an change the duplicated Lines to:
```
linux_entry "${OS} - Acceleration turned off" "${version}" simple \
    "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT} nouveau.noaccel=1"
```
3) edit /etc/default/grub
3a) change GRUB_HIDDEN_TIMEOUT=0 to ```
#GRUB_HIDDEN_TIMEOUT=0
```
4) run ```
sudo update-grub
```
5) reboot.

Hope someone will fix the nouveau Driver so that this awfull Workaround is not neccesery any more, but have little hope that someone will spend time into this old hardware.

Yours Gerd

---

