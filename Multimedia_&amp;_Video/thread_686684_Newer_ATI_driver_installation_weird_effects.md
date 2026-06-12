---
title: "Newer ATI driver installation: weird effects"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by perixx on 2008-02-03
Even after manually installing the driver (8.01, 7.11, 8.42.3, 8.40.1) and compiling the kernel module where needed, this command won't find any installed drivers, only the installed fglrx-kernel-module, the fglrx-kernel-module-source and fglrx-amdcccle: ```
dpkg -l fglrx*
``` How come that DPKG won't find installed Ati DRIVERS? Btw., under /usr/share/ati, there are NO drivers installed, only 'amdcccle'...

[Besides, I've followed all the instructions on [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), even tried the symlink-hack for Mesa.]

perixx

---

### Post by Giannis68 on 2008-02-03
**[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)**



**Install the Catalyst 8.1 Driver Manually**

 *This is just an alternative installation method for the section above. It might help if you still get 'DRI missing' errors.*  [LIST]
[*]Note: *If you are running the -rt kernel, you will fail to compile the kernel module with *"FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'"*.*[/LIST] Download the ATI driver installer: [ati-driver-installer-8-01-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-01-x86.x86_64.run") (this installer is for 32bit **and** 64bit systems) 
Change to the download directory.  Make sure that you have the *universe* and *multiverse* repositories enabled in */etc/apt/sources.list* before doing these steps.   
There is a detailed manual with screenshots at [Ubuntu Wiki]("https://wiki.ubuntu.com/AddingRepositoriesHowto"). 
By default, Ubuntu did not enable the Universe and Multiverse repositories, but now in Gutsy, both Universe and Multiverse are activated by default. 
*Install necessary tools:* 
 sudo apt-get update
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms
*Uninstall previous fglrx:*  Using Synaptic, completely remove any packages containing "fglrx" in their name.  
*Create .deb packages:*  
 sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy
note: if this step fails with a signal being caught, and you are running the script on an NFS-mounted directory, copy it to a local partition, and it will work. The same error may result from insufficient disk space. 
If this step fails on amd64/x86_64 with a No such file or directory message about missing files in X11R6/lib, [follow these instructions]("http://emmetcaulfield.net/Tech/Ubuntu64+ATI") and come back here. Also check that your downloadpath does not contain spaces. 
*Blacklist old fglrx module from linux-restricted-modules:* 
As Ubuntu Gutsy's *linux-restricted-modules* package includes the fglrx module from an old driver version (8.37.6), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead. 
Ubuntu/Gnome users type in: 
 gksu gedit /etc/default/linux-restricted-modules-common Kubuntu/KDE users type in: 
 kdesu kate /etc/default/linux-restricted-modules-common Add "fglrx" to the line "DISABLED_MODULES" 
    [SIZE=-1]**File:** /etc/default/linux-restricted-modules-common[/SIZE]    DISABLED_MODULES="fglrx"  Please note that after the modification above, the "Restricted Driver Manager" will signal "ATI accelerated grapichs driver" not enabled (unticked). This is perfectly correct. At the end of the installation procedure it will signal in Status: "in use" (green light), but NOT enabled. It simply means that the fglrx module contained in the linux-restricted-modules package is not enabled, but another fglrx module (7.12) is in use. 
You may also need to edit the file (if it exists): 
 sudo gedit /etc/modprobe.d/blacklist-restricted Put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration. 
*Remove any old fglrx debs from /usr/src/:* 
 sudo rm /usr/src/fglrx-kernel*.deb
*Install .deb packages:* 
 sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb

---

### Post by perixx on 2008-02-03
Thank you for your reply..!

I guess I can claim to have followed really EVERY single step you've suggested here, Giannis! Apart from the info on 'wiki.cchtml' - I'll go through all steps there again, but I don't think to find anything new. I've been following all the info on the ATI manual binary driver Howto and exercised all the steps there with ATI version 8.01 and 7.11 (and even with 7.12 before, I believe), as well as I've been trying all that drivers with Envy and even just by running the installer. 

At no time, the kernel module seems to have been installing properly (7.12 or 8.01, that is), unless I manually compiled it via modconf/module-assistant. Besides, I've even installed the DKMS package from Dell, which should take care of the kernel-module-compilation from version 7.12 on, or so I've read. Even after manual kernel compilation, 'dpkg -l fglrx*' wouldn't list any installed 'xorg-fglrx-driver' (though I've installed the respective compiled .deb package) - Synaptic will list them correctly. 

Consequentially, in /usr/share/ati, there won't be any 'fglrx' contents, also no 'fglrx-uninstall.sh'. Additionally, there seems to be '/usr/lib/libGL.so.1' and/or /usr/lib/xorg/modules/extensions/libglx.so missing, or wrong versions of those files, regardless or what I try... I'm really despaired!

Besides, before, I had installed a Nvidia card with 169.09 drivers and ever since that my problems started to grow - there was a lot of stuff remaining, which I had to remove by hand. Meanwhile, I've reinstalled nearly all of the underlying Linux-architecture... xubuntu-xorg, linux-kernel-common, linux-restricted-common... 

**ADD:** Also tested 8.42.3 and 8.40.1 drivers with same results by now!

perixx

---

### Post by Giannis68 on 2008-02-03
ok try to force install one older version...
open Synaptic find xorg-driver-fglrx mark driver Ctrl+E and force one older driver...

---

### Post by perixx on 2008-02-03
Hy again, Giannis!

As you see, I'm really desparate about this, for I've kinda started parallel threads, which I ususally don't like to...

I've reinstalled the 7.11 driver again, in the exact manner that was proposed here: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") 
I think an important step, that wasn't mentioned in the Ubuntu-Howto is that one: ```
sudo ln -s /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
``` After applying this, I hadn't got OpenGL support at all (no libGL.so.1 was found); so I've deleted the likewise-named false symlink and replaced it with   this one - I'm but not sure if that's Mesa or Ati stuff: ```
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
``` Afterwards, I rebooted and had MESA 1.4 OpenGL drivers (fglrxinfo). 

I tried to track down the source of the problem: > /var/log/Xorg.0.log | grep drm
(WW) fglrx(0): Cannot resolve drmOpen symbol.(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536

less /var/log/Xorg.0.log | grep dri
X.Org XInput driver : 0.7
(II) LoadModule: "dri"
(WW) Warning, couldn't open module dri
(II) UnloadModule: "dri"
(EE) Failed to load module "dri" (module does not exist, 0)
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
        ABI class: X.Org XInput driver, version 0.7
        ABI class: X.Org XInput driver, version 0.7
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) AMD Video driver is running on the exact device targeted for this release
(II) AMD Video driver is signed
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(WW) Warning, couldn't open module dri
(II) UnloadModule: "dri"
(EE) fglrx: Failed to load module "dri" (module does not exist, 0)
(==) fglrx(0): OpenGL ClientDriverName: "[COLOR="Red"]**fglrx_dri.so**[/COLOR]"
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *

dpkg -l fglrx*
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Säubern/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/Fehlgeschl. Konf./Halb install.
|/ Fehler?=(kein)/Halten/R=Neuinst notw/X=beide (Status, Fehler: GROSS=schlecht)
||/ Name           Version        Beschreibung
+++-==============-==============-============================================
ii  fglrx-amdcccle 8.433-1        Catalyst Control Center for the ATI graphics
pn  fglrx-control  <keine>        (keine Beschreibung vorhanden)
un  fglrx-control- <keine>        (keine Beschreibung vorhanden)
**[COLOR="Red"]un  fglrx-driver   <keine>        (keine Beschreibung vorhanden)[/COLOR]**
un  fglrx-driver-d <keine>        (keine Beschreibung vorhanden)
un  fglrx-kernel   <keine>        (keine Beschreibung vorhanden)
ii  fglrx-kernel-2 8.433-1+2.6.20 ATI binary kernel module for Linux 2.6.20-16
ii  fglrx-kernel-s 8.433-1        Kernel module source for the ATI graphics ac


As you can see, there's obviously no installed fglrx-**driver** found by dpkg, which is weird, because it IS installed, according to Synaptic. Also, '**fglrx_dri.so**' isn't found; one file like that is found in **/usr/lib/dri**, to which a folder-symlink is pointing from **/usr/lib/xorg/modules/dri **. Perhaps it is the right version, perhaps not, I can't judge. 

But the symlinking must be insufficient/wrong. I guess that all boils down to missing/wrong symlinks in the end... if I only knew WHICH ones!

ADD: > You also need to remove the xorg-driver-fglrx or your manually installed drivers to get the 3D acceleration back, since it is provided by file /usr/lib/libGL.so.1.2 which belongs to libgl1-mesa package and which is moved to backup Just stumbled upon this; I guess that means, that I've just symlinked to Mesa-OpenGL above... BUT... the other symlink in place was dead - why hasn't it been placed properly by the installer :? Ehh... 
Besides, /usr/lib/fglrx and /usr/share/ati are empty again...
THE FUNNY THING about THIS is, that I used the driver installer before, which resulted in at least having stuff in the latter one!

perixx

---

### Post by perixx on 2008-02-04
Here's my initial trouble-thread about the remaining Nvidia-crap on my system (partially solved):
[http://ubuntuforums.org/showthread.php?t=679086]("http://ubuntuforums.org/showthread.php?t=679086")

:arrow: I've tested from 8.01 (see: [http://ubuntuforums.org/showthread.php?p=4266273#post4266273]("http://ubuntuforums.org/showthread.php?p=4266273#post4266273"))
and 7.11 down to 8.42.3 and 8.40.1 all drivers with about the same results by now! Using the following methods AND Envy - CLI mode - (mostly all 3 ways) with about the same results:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

**INTRIGUING:** I've been able to install the 8.443.1 driver before on my system, just by running the installer...

**[COLOR="Red"]NOW[/COLOR]** I can't seem to get the restricted driver 8.34 'xorg-driver-fglrx' back to work again => Mesa only :(

perixx

---

### Post by perixx on 2008-02-04
**WELL**, I've finally made it back again to v. 8.34 standard FGLRX-drivers!!!

Since the usual 'saviour' wouldn save me this time:```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I've reinstalled a whole bunch of packages, just to make sure... > xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.6-16.30)
xorg-driver-fglrx-dev (7.1.0-8.34.8+2.6.20.6-16.30)
fglrx-kernel-source (8.34.8+2.6.20.6-16.30)
linux-restricted-modules-2.6.20-16-generic (2.6.20.6-16.30)
linux-restricted-modules-common (2.6.20.6-16.30)
linux-restricted-modules-generic (2.6.20.16.28.1)
restricted-manager (0.20)
linux-headers-2.6.20-16 (2.6.20-16.33)
linux-headers-2.6.20-16-generic (2.6.20-16.33)
xserver-xorg-core (2:1.2.0-3ubuntu8.3)
xserver-xorg-dev (2:1.2.0-3ubuntu8.3)
libdrm-dev (2.3.0-1)
libdrm2 (2.3.0-1)
libgl1-mesa-dri (6.5.2-3ubuntu8]
libgl1-mesa-glx (6.5.2-3ubuntu8]
libglib1.2 (1.2.10-17build1)
libglib1.2-dev (1.2.10-17build1)
module-init-tools (3.3-pre3-1ubuntu7)

Though I should know better, I'll give 8.40.1 a shot again... but NOT now ^^

perixx

---

### Post by perixx on 2008-02-04
**FANTASTIC!!!** FINALLY, I've been **able to install new drivers again!!**

I'm suspecting that the > xserver-xorg-core (2:1.2.0-3ubuntu8.3) was the main responsible package while reinstalling... but it could as well have benn anything else...

[COLOR="Blue"]**The INTERESTING thing is,**[/COLOR] I haven't been able to set up ANY of the newer drivers by compiling the .deb packages and installing them so far (at no time at all)! 

I've noticed the following: the .deb packages won't install /usr/share/ati/FILES, and will possibly also not compile the correct /usr/lib/dri/fglrx_dri.so file - where the installer will do that! Also, the folder-symlink /usr/X11R6/lib/modules/dri to /usr/lib/dri/fglrx_dri.so won't be created with any of the .deb packages, from what I've observed. 

Another missing link [might] be a missing symlink from /lib/modules/$(uname -r)/volatile to /lib/modules/$(uname -r)/misc/fglrx.ko (according to the troubleshooting section of the ATI binary driver installation page). But the 7.11 installer worked without creating such a symlink - it won't even create the folder /misc.

The ONLY way to install new ATI drivers was and is - guess - ```
sudo ./ati-driver-installer-...............run
```!!!!

perixx

---

