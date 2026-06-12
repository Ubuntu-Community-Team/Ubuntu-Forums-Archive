---
title: "ATI, NVidia and 3 monitors"
date: 2012-01-02
forum: Multimedia Software
---

### Post by xxtreem11 on 2012-01-02
Running Ubuntu server 10.04 with Ubuntu-Desktop packages installed.
I'm trying to get a 3 monitor setup here.  I have an ATI Radeon 2400 HD card running 2 monitors and an NVidia GeForce 6200 running the third one.  I've gotten the xorg.conf to a point where I can comment out the "Screen" line in the server layout and each card works fine separately.  Once I use then together, that's where X crashes. :(
According to my xorg log, I'm getting a seg fault.  Here's the error and backtrace:

Error:
(EE) Jan 02 09:46:20 NVIDIA(1): Failed to initialize the GLX module; please check in your X
(EE) Jan 02 09:46:20 NVIDIA(1):     log file that the GLX module has been loaded in your X
(EE) Jan 02 09:46:20 NVIDIA(1):     server, and that the module is the NVIDIA GLX module.  If
(EE) Jan 02 09:46:20 NVIDIA(1):     you continue to encounter problems, Please try
(EE) Jan 02 09:46:20 NVIDIA(1):     reinstalling the NVIDIA driver.


Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x45fcc8]
1: /usr/bin/X (0x400000+0x5dfbd) [0x45dfbd]
2: /lib/libpthread.so.0 (0x7f6f1abf7000+0xf8f0) [0x7f6f1ac068f0]
3: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f6f16282000+0x36d5d9) [0x7f6f165ef5d9]
4: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f6f16282000+0x341946) [0x7f6f165c3946]
5: /usr/lib/xorg/modules/drivers/nvidia_drv.so (0x7f6f16282000+0x34e3e2) [0x7f6f165d03e2]
6: /usr/bin/X (AddScreen+0x1d4) [0x43f274]
7: /usr/bin/X (InitOutput+0x7b4) [0x46dff4]
8: /usr/bin/X (0x400000+0x26005) [0x426005]
9: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f6f198efc4d]
10: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting


I've got my xorg.conf file attached.

I'm guessing I have a conflict between the NVidia glx and the ATI glx modules, but I'm not sure how to fix it.  
Please help!

---

### Post by xxtreem11 on 2012-01-04
Bumpy bump?

---

### Post by BicyclerBoy on 2012-01-04
As I understand it .. it is not possible to use 2 glx drivers in the same X server..

I don't think the Xorg X server tries to do this..
32 bit systems can run out of allocated ram with multiple video cards..you can allocate more with grub option.

The sharing of multiple GPU in same X server is only possible with similar/same GPU & with support in the video driver.
Normally all gl/glx acceleration is done on the primary card.

You can have multiple X servers on one computer..The programs may not run or be usable without server focus..

Remove the "glx" from the modules section..it is loaded automatically.

Post the /var/log/Xorg.0.log file..

---

