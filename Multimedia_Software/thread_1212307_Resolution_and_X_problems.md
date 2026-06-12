---
title: "Resolution and X problems"
date: 2009-07-13
forum: Multimedia Software
---

### Post by snowishberlin on 2009-07-13
Help!  Please!  I feel like I have tried everything suggested here and elsewhere to no avail.  The story: today I bought a new hard drive, and rather than work from a backup, I just thought, 'wouldn't a fresh install be nice?  I've been upgrading since 7.04, and maybe I want to start, well, fresh!'  So I did.  And I cannot get my resolution higher than 1280x800.  And that is not fair at all.  Yesterday with 9.04(upgraded version) I had at least 1280x1024, if not higher.  Now with 9.04(fresh version) I have this crappy stuff.  So what did I lose?
  I have a Lenovo 3000 N100 with a Geforce GO 7300 video card.
  I have tried downloading and running/installing the NVIDIA package, 'NVIDIA-Linux-x86-185.18.14-pkg1.run' from NVIDIA, which leads me to compile a kernel module, which fails.
  I can't run nvidia-xconfig because I don't seem to have it, and I can't find it anywhere, like to download or install.
  I have tried the help here: [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368) and it didn't work, because of the kernel problem.
  System>Admin>NVIDIA X Server Settings yields absolutly nothing that I can change or modify.
  Xrandr seems like it might be the salvation, but I am just not getting it.  Xrandr's output is:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1

/etc/X11/xorg.conf's output is: 
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
--essentially nothing.

  Does anyone have any other suggestions or workarounds or cheats or special hammers to beat the drivers with?  Any help would be great.  Thanks.

---

### Post by Vakman on 2009-07-13
Let's try to install the drivers again.
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run
```
Then run
```
sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run
```
If you have the x64 version of Ubuntu then add "_x64 after where ever it says x86, change it to x86_64.

---

### Post by snowishberlin on 2009-07-13
Thisislaw: That gets me nearly the same errors as before with the kernel module compiling error... 

" ERROR: You appear to be running an X server; please exit X before          
         installing.  For further details, please see the section INSTALLING 
         THE NVIDIA DRIVER in the README available on the Linux driver       
         download page at [www.nvidia.com]("http://www.nvidia.com").
 ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find          
         suggestions on fixing installation problems in the README available 
         on the Linux driver download page at www.nvidia.com."

The log: 
"nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Jul 13 22:23:36 2009
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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 185.18.14
         NVIDIA Linux graphics driver installed in this system.  For further
         details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in
         the README available on the Linux driver download page at
         [www.nvidia.com]("http://www.nvidia.com").
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '4997'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com]("http://www.nvidia.com").
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com."


And that makes me think that even if I stopped gdm to run it, I would get the same result.

Yes, I have the 32bit.

---

### Post by Vakman on 2009-07-13
Hm, interesting. I agree with you even if you stopped to run it you would get an error.
We should remove any other drivers you have installed though to do it fresh. You could try installing the drivers through EnvyNG if you haven't already. So that we know what we have no previous things in the way
We would like the xserver to be back to default and worry about the actually driver installation afterwards.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will put the xserver back to it's default.
Also try ```
sudo apt-get remove nvidia-glx
```
Then attempt to reinstall the drivers whichever way you like, method above, or EnvyNG.

---

### Post by snowishberlin on 2009-07-13
ThisisLaw,
  Superbly interesting, I would say.  That did not work, and using Envy and trying to use each of its options only brought me to error screens, mostly stating (EE) No devices detected.  And then I had to deal with loading gdm in low graphics mode, reset to default, and then restart yet again.  I did restart after every change, too.
  Anything else?  And thanks for the help so far!

---

### Post by Vakman on 2009-07-13
Ha, no problem but I haven't done much.
There is a Howto but it is rather a long one. But worth a try. 
[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)
How to for how to install the 185.18 driver. Worth a shot :P

---

### Post by snowishberlin on 2009-07-14
No, sigh, that didn't work, either.  That led to the same problem with compiling and the NVIDIA tool.  It did say that it didn't detect a compatible device on my machine before it tried to compile on its own, but I think that is normal, and hence the compilation.

---

### Post by snowishberlin on 2009-07-14
May I just make a complete *** of myself and post lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

  So it seems that I have an Intel card instead(and I am very very sorry for this mistake), but trying to get drivers for this card, or to get the resolution ramped up again is still not working.  Maybe we could call this a redirection?

---

### Post by Vakman on 2009-07-15
Aha, not a problem but that would be the issue :P
Also here we go again. I wish you had a nVIDIA card...
Intel Graphics and 9.04 didn't play nice.
Try this and follow it [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Let me know how that goes.

---

### Post by snowishberlin on 2009-07-25
I give up.  The resolution isn't that bad.  I had an expert around last weekend who worked on it for an hour or two, but nothing better than 1280x800.  Thanks anyway!

---

