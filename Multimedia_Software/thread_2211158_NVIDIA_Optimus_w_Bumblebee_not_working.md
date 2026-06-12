---
title: "NVIDIA Optimus w/ Bumblebee not working"
date: 2014-03-14
forum: Multimedia Software
---

### Post by jsvcycling on 2014-03-14
I just purchased a custom Toshiba Qosmio X70-A from Toshiba (I only changed the i5 to an i7, everything else is standard). I've installed Ubuntu successfully, but I can't seem to get Bumblebee to work. I reinstalled Ubuntu twice and in both instances I come to the same error even though I took differet paths to get to them.

When I run:
```
optirun -vv glxgears
```

I get:
```
[  521.802548] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[  521.803176] [INFO]Configured driver: nvidia
[  521.803398] [DEBUG]optirun version 3.2.1 starting...
[  521.803487] [DEBUG]Active configuration:
[  521.803526] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[  521.803567] [DEBUG] X display: :8
[  521.803601] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-304-updates:/usr/lib32/nvidia-304-updates
[  521.803629] [DEBUG] Socket path: /var/run/bumblebee.socket
[  521.803656] [DEBUG] Accel/display bridge: auto
[  521.803688] [DEBUG] VGL Compression: proxy
[  521.803714] [DEBUG] VGLrun extra options: 
[  521.803758] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[  521.803857] [DEBUG]Using auto-detected bridge primus
[  522.078821] [INFO]Response: No - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  522.078843] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[  522.078851] [DEBUG]Socket closed.
[  522.078873] [ERROR]Aborting because fallback start is disabled.
[  522.078885] [DEBUG]Killing all remaining processes.
```

Running this:
```
inxi -G
```

returns:
```
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller 
           X.Org: 1.14.5 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.5hz 
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 10.2.0-devel
```

And running:
```
lspci | egrep '3D|VGA'
```

returns:
```
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 770M] (rev a1)
```

I am using a fresh install of bumblebee, bumblebee-nvidia, and nvidia-current-updates.

I tried several tactics (adding acpi=force in GRUB didn't do anything) but to no avail.

Any help will be greatly appreciated. If you'd like more information, just let me know and I'll post it.

---

### Post by jsvcycling on 2014-03-14
After some more research, I am attempting to install 13.04 (I previously had 13.10) as it seems that Linux Kernel 3.10+ has issues with Bumblebee (despite the fact that it is officially supported on Ubuntu 13.10).

---

### Post by Yellow Pasque on 2014-03-15
> /usr/lib/nvidia-304-updates
You were using the older "legacy" 304.xx branch of nvdia driver, which does not support 700M series, so 13.10 may very well have worked if you had used 319.xx branch (or newer).

---

