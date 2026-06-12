---
title: "X11 segfault with tri monitor dual gpu"
date: 2011-07-31
forum: Multimedia Software
---

### Post by Matpen on 2011-07-31
hi all!

I have tried to setup a workstation with 3 monitors on two ati videocards, the goal being to span the desktop across all of them.

The process was not difficult at all, but after login X11 crashes and I am left with a console. I am fortunately able to login in safe mode, but I would like to ask for help in debugging this issue.

Here I will try to give as much detail as possible, starting with my system specifications:

```

matteo@matteo-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

matteo@matteo-desktop:~$ uname -mrs
Linux 2.6.38-10-generic x86_64
matteo@matteo-desktop:~$

matteo@matteo-desktop:~$ lspci|grep VGA
04:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
05:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]

```

The first card, the ATI Radeon HD 4650 is capable of running two monitors at the same time.
The monitors, for all it matters, are three identical ACER P206HV 20" connected with their analog interface (due to missing cables #-o which I will buy soon). Resolution 1600x900 each.
My motherboard is an AsRock 870 Extreme3 mounting an AMD Athlon II X4 640  3 GHz processor and 8 GB of RAM.

When asked by Ubuntu, I installed the ATI Caralyst driver version 11.6 and set it up for using Xinerama.

As I said, this setup works fine if I login in safe mode, but crashes X11 otherwise (even in classical mode - no Unity). By inspecting the logs (attached) I found this (notice the segfault)
```

[...]
[  1937.756] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[  1937.756] (II) fglrx(1): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[  1946.647] 
Backtrace:
[  1946.647] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a2656]
[  1946.647] 1: /usr/bin/X (0x400000+0x621ca) [0x4621ca]
[  1946.647] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f6e0fa9d000+0xfc60) [0x7f6e0faacc60]
[  1946.647] 3: /usr/bin/X (0x400000+0xb9ab4) [0x4b9ab4]
[  1946.647] 4: /usr/bin/X (0x400000+0x2e2a9) [0x42e2a9]
[  1946.647] 5: /usr/bin/X (0x400000+0x21a7e) [0x421a7e]
[  1946.647] 6: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xff) [0x7f6e0e9e6eff]
[  1946.648] 7: /usr/bin/X (0x400000+0x21629) [0x421629]
[  1946.648] Segmentation fault at address 0x4
[  1946.648] 
Caught signal 11 (Segmentation fault). Server aborting
[  1946.648] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  1946.648] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  1946.648] 
[  1946.780] (II) Power Button: Close
[  1946.780] (II) UnloadModule: "evdev"
[  1946.780] (II) Unloading evdev
[  1946.780] (II) Power Button: Close
[  1946.780] (II) UnloadModule: "evdev"
[  1946.780] (II) Unloading evdev
[  1946.790] (II) sonixj: Close
[  1946.790] (II) UnloadModule: "evdev"
[  1946.790] (II) Unloading evdev
[  1946.801] (II) Logitech USB Optical Mouse: Close
[  1946.801] (II) UnloadModule: "evdev"
[  1946.801] (II) Unloading evdev
[  1946.810] (II) AT Translated Set 2 keyboard: Close
[  1946.810] (II) UnloadModule: "evdev"
[  1946.810] (II) Unloading evdev
[  1946.810] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1946.810] (II) fglrx(0): Backup framebuffer data.
[  1946.811] (II) fglrx(0): Backup complete.
[  1947.345] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1947.345] (II) fglrx(1): Backup framebuffer data.
[  1947.346] (II) fglrx(1): Backup complete.
[  1947.398]  ddxSigGiveUp: Closing log

```

As a test, I tryed to configure Catalyst without Xinerama, an this works, but of course I end up with two separate desktop, which is not what I want.
In this mode, xrandr seems to work correctly
```

Screen 0: minimum 320 x 200, current 3200 x 900, maximum 3200 x 3200
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x900+1600+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       59.9*+
   1152x864       60.0 +   75.0  
   1440x900       59.9  
   1280x800       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
CRT2 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       59.9*+
   1152x864       60.0 +   75.0  
   1440x900       59.9  
   1280x800       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)

```

After some research I found that XRandR does not support desktop spanning over multiple GPUs, so Xinerama is the only way to go in my case. Since the two are not compatible with each other, after login in safe mode I see that XRandR is disabled
```

matteo@matteo-desktop:~$ xrandr -v
xrandr program version       1.3.4
RandR extension missing

```

One more test consisted in disabling the XRandR module in the config files, as found in some posts:
edits in /etc/X11/xorg.conf
```

[...]
Section "ServerFlags"
        Option "RandR" "off"
        Option "Xinerama" "on"
EndSection
[...]
Section "Device"
        Option      "EnableRandR12"  "false"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        Option      "OverlayOnCRTC2" "1"
        Option      "Monitor-CRT1" "0-CRT1"
        Option      "Monitor-CRT2" "0-CRT2"
        BusID       "PCI:4:0:0"
EndSection
Section "Device"
        Option      "EnableRandR12"  "false"
        Identifier  "aticonfig-Device[1]-0"
        Driver      "fglrx"
        Option      "Monitor-CRT2" "1-CRT2"
        BusID       "PCI:5:0:0"
EndSection
[...]

```
configuring the ati driver:
```

sudo aticonfig --set-pcs-str="DDX,EnableRandR12,FALSE"

```

but this did not help.

So now I am wondering which other cause can the segfault have.
Any help would be greatly appreciated!

---

### Post by Matpen on 2011-08-04
Bump... anyone?

---

### Post by lgadani on 2011-08-11
I have the same problem (same backtrace). I'm using 3 monitors with 1 AMD Radeon 6950. Running Ubuntu Natty, Catalyst is the default one from Ubuntu.

Did you find any solution?

---

### Post by Matpen on 2011-08-23
Unfortunately not... I hope that someone will point me in the right direction, since I am complitely stuck with this problem.

Maybe someone knows a good place to post this issue?

---

