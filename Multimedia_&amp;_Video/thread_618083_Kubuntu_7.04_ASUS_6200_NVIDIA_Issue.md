---
title: "Kubuntu 7.04 ASUS 6200 NVIDIA Issue"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by lazer on 2007-11-20
Here's the issue.  I recently did a clean install of Kubuntu 7.04 (Fiesty Fawn).  I'm running kernal 2.6.20-16 (sorry I'm on my computer at home so I can't look it up right now, I'll post updated info tomarrow morning).  Now I have a ASUS graphics card that has an NVIDIA Geforce 6200 Turbocache 256MB card.  I tried using the restricted drivers.  After running "nvidia-config" I reboot X and here's where things get strange.

The Kubuntu loading bar shows up for a bit (no appears to be happening with the bar) then I get a black screen with a blinking white cursor in the upper left corner.  I switch to the command line and I see that KDM is running but that's about it.  If I switch back to my old xorg.conf I can reboot with the screen working but no graphics card acceleration.

My monitor is a 19" LCD.  I'm running it off the DVI port on the card.

I've seen this problem mentioned once before but no response was given.  Any ideas?  I'll post up more specific info later.

---

### Post by lazer on 2007-11-20
Here's some info:
```

$lspci -n | grep 0300
01:00.0 0300: 10de:0161 (rev a1)
$uname -r
Linux ******** 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

```
The Card is an NVIDIA 6200 Turbocache by ASUS
01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)] (rev a1)
The card says the following on it:
EN6200TC256/TD/64M/A

---

### Post by lazer on 2007-11-20
Tried the driver from NVIDIA's site (100.14.19).  Still no luck.  Any help?

---

### Post by lazer on 2007-11-20
Bump for help here.

---

### Post by lazer on 2007-11-21
I think I may have tracked down the issue.  Neither the nVidia supplied drivers nor the drivers in the ubuntu repositories work.  And I think the issue is a bit involved.  First let me remind you that I'm running kernel:
2.6.20-16-generic
Now I downloaded 
nvidia-kernel-common_20051028+1ubuntu7_all.deb
and installed the common kernel without issue.  Next I downloaded
nvidia-glx-new_1.0.9755+2.6.20.6-16.30_i386.deb
which is the appropriate package for this card and my kernel.  However, when I try to install it I get the following:
```
Selecting previously deselected package nvidia-glx-new.
(Reading database ... 109922 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.6-16.30_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-glx-new:
 nvidia-glx-new depends on nvidia-kernel-1.0.9755; however:
  Package nvidia-kernel-1.0.9755 is not installed.
  Package linux-restricted-modules-2.6.20-15-generic which provides nvidia-kernel-1.0.9755 is not installed.
  Package linux-restricted-modules-2.6.20-16-generic which provides nvidia-kernel-1.0.9755 is not installed.
  Package linux-restricted-modules-2.6.20-15-386 which provides nvidia-kernel-1.0.9755 is not installed.
dpkg: error processing nvidia-glx-new (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-glx-new
Press <enter> to exit...

```
Before when I used adept to try and install everything I didn't pay attention to it's attempt to install:
linux-restricted-modules-2.6.20-15-generic
instead of
linux-restricted-modules-2.6.20-16-generic
so I think this was the issue.

---

### Post by lazer on 2007-11-21
Still no dice.  Even with the proper restricted packages things are screwy.  Again here's what happens.  If I switch "nv" to "nvidia" in the xorg.conf and reboot the Xserver I get a Kubuntu splash screen with progress bar.  The progress bar makes no progress....then I get a black screen with white cursor.  Somebody has to know what's wrong here.

tail -f /var/log/messages
```
Nov 21 10:44:30 dust kernel: [66165.026546] NVRM: this kernel module has the version 1.0-9631.  Please
Nov 21 10:44:30 dust kernel: [66165.026547] NVRM: make sure that this kernel module and all NVIDIA driver
Nov 21 10:44:30 dust kernel: [66165.026548] NVRM: components have the same version.
Nov 21 10:45:25 dust kernel: [66219.537774] mtrr: type mismatch for c0000000,4000000 old: write-back new: write-combining
Nov 21 10:45:46 dust gconfd (lazersos-20626): starting (version 2.18.0.1), pid 20626 user 'lazersos'
Nov 21 10:45:46 dust gconfd (lazersos-20626): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 21 10:45:46 dust gconfd (lazersos-20626): Resolved address "xml:readwrite:/home/lazersos/.gconf" to a writable configuration source at position 1
Nov 21 10:45:46 dust gconfd (lazersos-20626): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 21 10:45:46 dust gconfd (lazersos-20626): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 21 10:45:46 dust gconfd (lazersos-20626): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4

```

---

### Post by lazer on 2007-11-21
Issue not resolved but I can't waste any more time so here's the workaround.


Use kernel 2.6.20-15

In this kernel I can use adept to grab nvidia-glx-new then us nvidia-glx-config enable....restart X and I have a working card.  Boot into 2.6.20-16 and I get bubkiss. This works for now.  Should I get a grant and need to purchase new computers......I'll be buying Apple products.

---

### Post by lazer on 2008-02-12
Well I've had a bit more time and dug a little deeper.  So here's my kdm log:

When I try to boot into 2.6.20-16 here's what happens:
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dust.net.gi.alaska.edu 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 12 11:55:41 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "wfb" (module does not exist, 0)
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

```

I go to 2.6.20-15 and I get:
```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dust.net.gi.alaska.edu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 12 11:59:22 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "wfb" (module does not exist, 0)
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by lazer on 2008-02-12
Just a note I don't have a wacom tablet and I realized that Ubuntu didn't install the device drivers by default so I'm installing those so it won't complain (instead of just commenting them out as the X.org config assumes they exist anyway).

---

### Post by lazer on 2008-02-12
Apparently there is some issue with loading the 'wfb' module.

So 2.6.20-16 fails to load the Nvidia kernel module.

---

