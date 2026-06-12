---
title: "RadeonHD open-source 3D Guide (EXPERIMENTAL)"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Yellow Pasque on 2009-09-03
**PURPOSE AND OVERVIEW**
----------------------------------------
- This guide is for people who want to try the latest open-source, hardware-accelerated 3D code on their ATI RadeonHD (R600/R700) GPU. At the time of this writing, the r600 mesa driver only supports OpenGL 1.4, DO NOT expect 3D performance gains or extra features over fglrx/Catalyst drivers (though the open-source drivers may work better in other areas).
- I have personally used this guide (successfully) on Ubuntu 9.04, Ubuntu 9.10, and Debian sid(ux).
----------------------------------------

**STATUS OF SOME 3D PROGRAMS**
----------------------------------------
Reference: [http://wiki.x.org/wiki/radeonhd%3Aexperimental_3D](http://wiki.x.org/wiki/radeonhd%3Aexperimental_3D)
```
# googleearth: runs ok, start this program from the terminal with vblank_mode=0 (thanks to John Bridgman @ AMD for the tip)
# glxgears: runs, I get ~1800fps on a RadeonHD4550, (glxgears isn't a good benchmark to compare different systems because of its CPU dependence)
# neverball: runs, nice!
# savage2: doesn't run,
    * Savage2 - Fatal Error: OpenGL 2.0 not available.
    * Savage2 - Fatal Error: Segmentation Fault
    * Segmentation fault (core dumped) 
# ETQW: doesn't run;
    * ERROR: The current video card / driver combination does not support the necessary features: GL_ARB_occlusion_query 
# sauerbraten: starts, switches to graphics mode, starts initialize shaders and hangs after a while (Alt-SysRq-B only works)
# trophy: runs, playable, ok
# tremulous: works, playable, fast! 
# compiz: starts and runs, most effects work (blur may not), gnome-terminal suffers from invisible characters (I personally have not noticed this)
# openarena: works, playable, fast, ok!
```
----------------------------------------


**ISSUES/DISCLAIMER**
----------------------------------------
- DO NOT do this on production systems. You probably shouldn't do this on your main install if borking it would be a huge problem for you. I wouldn't even recommend this to anyone but those that like to experiment and don't mind if their install gets messed up. BOTTOM LINE: Please don't send me angry PM's if this screws up your system. 
- This guide overwrites Ubuntu's default mesa install. I believe there is a way to keep the git code and the Ubuntu stuff separate (suggestions welcome).
- A special note for LAPTOP and owners of PASSIVELY-cooled GPU's: The open-source drivers currently only have limited dynamic power management. This can cause your GPU to run significantly warmer than it would with the proprietary drivers, which use AMD/ATI's PowerPlay technology for dynamic volting/clocking. (The open-source devs are currently working on implementing PowerPlay features, but they face a lack of documentation on this feature). BOTTOM LINE: You've been warned. Please don't send me angry PM's if this burns up your GPU.
----------------------------------------


**PURGING PROPRIETARY DRIVERS** (skip to the next section if you've never installed fglrx/Catalyst on your system)
----------------------------------------
- Previous or current installations of ATI's proprietary Catalyst/fglrx drivers are known to interfere with the installation of the open-source drivers. If you manually downloaded and installed drivers from AMD/ATI, run the following command first:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
- Now purge the Ubuntu fglrx packages (you WILL lose any custom configuration settings of these packages):
```
sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```
- This command is necessary to replace some proprietary libraries that fglrx leaves behind.
```
sudo apt-get --reinstall install libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```
- Finally, use this command to make sure you have a "clean" xorg.conf file (and back up your existing one)
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
- If you had special options for your input devices in your previous xorg.conf, you'll probably want to put them in the new one. At this point, restart your system and make sure you get the correct resolution and direct rendering works (look at /var/log/Xorg.0.log if you're unsure).
----------------------------------------


**PREREQUISITES**
----------------------------------------
- Before you begin, make sure your package information and system are updated.
```
sudo apt-get install linux-headers-`uname -r` freeglut3-dev x11proto* xutils-dev autoconf libltdl7-dev libpciaccess-dev libdrm-dev git-core gawk xorg-dev libgl1-mesa-dev pciutils-dev libglu1-mesa-dev pkg-config
```
- Before you build the DRM kernel modules, I suggest you back up your existing ones:
```
cd /lib/modules/`uname -r`/kernel/drivers/gpu/drm/
cp drm.ko radeon/radeon.ko ~/
cd ~/
tar -czf drm-modules.tar.gz drm.ko radeon.ko
```
----------------------------------------

**GETTING A RECENT 2D/MODESETTING DRIVER**
----------------------------------------
You can either use the ati/radeon or radeonhd driver. I prefer to use [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
----------------------------------------

**ALEX DEUCHER's (aka agd5f) DRM, INITIAL BUILD**
----------------------------------------
```
cd /opt
sudo git clone git://anongit.freedesktop.org/~agd5f/drm
cd drm
sudo git checkout -t -b r6xx-r7xx-3d origin/r6xx-r7xx-3d
sudo ./autogen.sh --prefix=$(pkg-config --variable=prefix libdrm) --libdir=$(pkg-config --variable=libdir libdrm) --includedir=$(pkg-config --variable=includedir libdrm)
sudo make
sudo make install
cd linux-core/
sudo make radeon.o drm.o
sudo make install
sudo cp drm.ko /lib/modules/`uname -r`/kernel/drivers/gpu/drm/
sudo cp radeon.ko /lib/modules/`uname -r`/kernel/drivers/gpu/drm/radeon
sudo depmod -a
```
----------------------------------------

**MESA, INITIAL BUILD**
----------------------------------------
- In this guide, we only build the Mesa software rasterizer (to fall back on) and the r600 DRI 3D module for r600/r700 cards (and should include r800 cards in the future). We do this to speed compilation significantly. If you need other DRI drivers, be sure to build/install them by either adding them to the --with-dri-drivers list or omitting that flag completely to build all available DRI drivers.
```
sudo mv /usr/lib/pkgconfig/libdrm_radeon.pc /usr/lib/pkgconfig/libdrm_radeon.pc.copy #It's okay if you get file not found
cd /opt
sudo git clone git://anongit.freedesktop.org/mesa/mesa
cd mesa
sudo ./autogen.sh --with-dri-drivers=swrast,r600 --libdir=/usr/lib/ --includedir=$(pkg-config --variable=includedir dri) --disable-gallium --disable-egl --enable-debug
sudo make
sudo make install
```

**TRYING IT OUT**
- For some reason, I find this necessary after everything is built:
```
cd /opt/drm
sudo make install
cd /opt/mesa
sudo make install
```
- Now you can restart your system and check glxinfo.
```
glxinfo | grep renderer
```
Should report 'Mesa DRI R600...'. (If you see 'Software Rasterizer', something went wrong; check your /var/log/Xorg.0.log). Hopefully, all is well and you can enjoy 3D stuff.
----------------------------------------


**UPDATING DRM**
----------------------------------------
Check this page to see if any updates have been pushed since you last built it: [http://cgit.freedesktop.org/~agd5f/drm/?h=r6xx-r7xx-3d](http://cgit.freedesktop.org/~agd5f/drm/?h=r6xx-r7xx-3d)
```
cd /opt/drm
sudo git pull
sudo make clean
sudo make install
cd linux-core/
sudo make clean
sudo make radeon.o drm.o
sudo cp drm.ko /lib/modules/`uname -r`/kernel/drivers/gpu/drm/
sudo cp radeon.ko /lib/modules/`uname -r`/kernel/drivers/gpu/drm/radeon
sudo depmod -a
```
----------------------------------------

**UPDATING MESA**
----------------------------------------
- Mesa is under heavy development and is being updated very frequently: [http://cgit.freedesktop.org/mesa/mesa/](http://cgit.freedesktop.org/mesa/mesa/) Before you report a bug, make sure your copy is updated.
- Remember to modify --with-dri-drivers flag to your needs (like in the initial build)
```
cd /opt/mesa
sudo git pull
sudo make clean
sudo mv /usr/lib/pkgconfig/libdrm_radeon.pc /usr/lib/pkgconfig/libdrm_radeon.pc.copy #Again, the file may not exist
sudo ./autogen.sh --with-dri-drivers=swrast,r600 --libdir=/usr/lib --includedir=$(pkg-config --variable=includedir dri) --disable-gallium --disable-egl --enable-debug
sudo make
sudo make install
```
----------------------------------------

**TODO**
----------------------------------------
A reverting procedure for people who want to go back to Ubuntu defaults.

---

### Post by Yellow Pasque on 2009-09-06
There is currently an issue when building Mesa from git because of this commit: [http://cgit.freedesktop.org/mesa/mesa/commit/?id=859828cc4fb989bc5b67d26991a090a9f37e7c05](http://cgit.freedesktop.org/mesa/mesa/commit/?id=859828cc4fb989bc5b67d26991a090a9f37e7c05)
I worked around the issue by opening the configure.ac file in a text editor. Towards the top, you'll see:
```
LIBDRM_REQUIRED=2.4.15
```
Change it to:
```
LIBDRM_REQUIRED=2.4.3
```
Re-run autogen.sh after you make the change.

EDIT: The newer version of libdrm is only required for intel GPU's.

---

### Post by Yellow Pasque on 2009-10-01
Edit: Nvm

---

### Post by EJeanmaire on 2009-10-06
Looks promising, kinda surprised there aren't any replies as of yet.  However, I cannot seem to get compiz going with this...

1.  What does your xorg.conf look like? 

2.  The parameters libdir and includedir didn't want to work when I ran this command... *sudo ./autogen.sh --with-dri-drivers=swrast,r600 --libdir=/usr/lib --includedir=$(pkg-config --variable=includedir dri) --disable-gallium --disable-egl --enable-debug*

3.  FYI, I had to sudo this command to make it work: *git clone git://anongit.freedesktop.org/mesa/mesa*

---

### Post by Yellow Pasque on 2009-10-06
1.```
Section "Device"
	Identifier	"Configured Video Device"
	Driver   "radeonhd"
        Option   "DRI"
        Option   "AccelMethod"  "EXA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "ServerFlags"
        Option     "DontZap"       "false"   #Allows Ctrl-Alt-Backspace to reset X server
EndSection
```

2. What is the output/error when you do that?

3. Fixed. Thanks.

---

### Post by Cerberus108 on 2009-10-09
Thanks for the guide, I'm really looking forward to try it. At the moment, I'm stuck at compiling drm.o, it seems the developer is just a little bit heedless: I've got a whole load of errors in "drm_pciids.h", something like this: 
```

...
/opt/drm/linux-core/drm_pciids.h:1476: error: expected identifier or ‘(’ before ‘{’ token
/opt/drm/linux-core/drm_pciids.h:1476: error: expected identifier or ‘(’ before ‘,’ token
/opt/drm/linux-core/drm_pciids.h:1485: error: expected identifier or ‘(’ before ‘{’ token
/opt/drm/linux-core/drm_pciids.h:1485: error: expected identifier or ‘(’ before ‘,’ token
...

```
I checked those lines in the file, and although I'm definitely NOT a C guru, it seems to be ok. Here's an example of buggy code lines:
```

    {0x10DE, 0x009C, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009C, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009D, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009D, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009E, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \

```
Can anyone help me? Do anyone other experience this problem? Thank you in advance!

---

### Post by Cerberus108 on 2009-10-09
> **Cerberus108 said:**
> Thanks for the guide, I'm really looking forward to try it. At the moment, I'm stuck at compiling drm.o, it seems the developer is just a little bit heedless: I've got a whole load of errors in "drm_pciids.h", something like this: 
```

...
/opt/drm/linux-core/drm_pciids.h:1476: error: expected identifier or ‘(’ before ‘{’ token
/opt/drm/linux-core/drm_pciids.h:1476: error: expected identifier or ‘(’ before ‘,’ token
/opt/drm/linux-core/drm_pciids.h:1485: error: expected identifier or ‘(’ before ‘{’ token
/opt/drm/linux-core/drm_pciids.h:1485: error: expected identifier or ‘(’ before ‘,’ token
...

```I checked those lines in the file, and although I'm definitely NOT a C guru, it seems to be ok. Here's an example of buggy code lines:
```

    {0x10DE, 0x009C, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009C, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009D, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009D, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \
    {0x10DE, 0x009E, PCI_ANY_ID, PCI_ANY_ID, 0, 0, NV40}, \

```Can anyone help me? Do anyone other experience this problem? Thank you in advance!

Nevermind, it compiled everything fine.. But i'm now stuck at this:

```

$ dmesg | grep drm
[    2.142412] [drm] Initialized drm 1.1.0 20060810
[    2.158726] [drm] radeon kernel modesetting enabled.
[    2.160163] [drm] radeon: Initializing kernel modesetting.
[    2.160167] [drm:radeon_driver_load_kms] *ERROR* Failed to initialize radeon, disabling IOCTL

```

Which causes Xorg to fail with drm:
```

$ cat /var/log/Xorg.0.log | grep drm
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
(EE) RADEONHD(0): RHDDRIVersionCheck: drmOpen("radeon", "pci:0000:01:00.0") failed.

```
Any help? I really want to try these drivers...

---

### Post by Yellow Pasque on 2009-10-09
Close your applications and log out. THen switch to a terminal (Ctrl+Alt+F1) and run:
```
sudo stop gdm
sudo modprobe -r radeon drm
sudo modprobe radeon modeset=0
sudo start gdm
```

If this works, you can permanently disable KMS (kernel mode-setting) by adding radeon.modeset=0 to your boot string in GRUB: [https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation)

---

### Post by Cerberus108 on 2009-10-10
Ok, I tried several ways to start X, here's what i got: 

[LIST]
[*]KMS disabled: flawless boot, at login time it starts loading the session but suddenly it falls back to gdm. Trying to switch to tty causes xorg to freeze, giving me something like a static screenshot instead of the login CLI shell.
[*]KMS enabled (from grub, booting with the "radeon.modeset=1" option): apparently flawless boot, actually drm gives me that error, the tty is unusable because of graphical glitches, at shutdown time the white ubuntu logo (I'm using karmic beta) is bad drawn, its colours seems to be corrupted as if i were using the vesa driver.
[/LIST]
It seems really annoying, doesn't it? I would like very much to be indipendent from fglrx driver...

---

### Post by H_a_D_3_z on 2009-10-10
This RadeonHD open-source guide that is referenced here, is it the same thing as the new xf86-video-RadeonHD-1.3.0 that just came out yesterday.  If not than you may be interested in looking at it.  I haven't been able to get it compiled correctly.  But, maybe one of you guys can get it running and share your ideas.:KS

---

### Post by Yellow Pasque on 2009-10-10
> This RadeonHD open-source guide that is referenced here, is it the same thing as the new xf86-video-RadeonHD-1.3.0 that just came out yesterday.
No, the driver will only provide 2D acceleration for RadeonHD cards. You need a special version of Mesa and a compatible kernel DRM for 3D hardware acceleration.

---

### Post by Yellow Pasque on 2009-10-10
> **Cerberus108 said:**
> KMS disabled: flawless boot, at login time it starts loading the session but suddenly it falls back to gdm. Trying to switch to tty causes xorg to freeze, giving me something like a static screenshot instead of the login CLI shell.

Can you log into an 'xterm' session and view/save logs? Note that there were Ubuntu updates to the kernel and Mesa recently (which might have overwritten your custom install), so I would recommend you follow the 'Updating DRM and Mesa' instructions.

> KMS enabled...
What kind of video card do you have? I don't think KMS should be enabled by default for RadeonHD cards. I have a fresh install of Karmic on a system with a RadeonHD 4550 (RV710) and KMS is disabled by default. I have not tried to install 3D support yet (though it worked fine on another Karmic install), but I will soon and let you know how it goes.

---

### Post by Cerberus108 on 2009-10-11
I am still experiencing that problem, I would really like to know if I am not the only one.. I am using a hd3650, which should be supported by the unstable release of these drivers. This is really disappointing, since noone seems to be interested in it. I don't even know who to ask for information or where to submit this "bug". Please, help me

---

### Post by Yellow Pasque on 2009-10-11
Bug reports go to freedesktop.org.
I also find Phoronix.com to be a good source of information.

---

### Post by monraaf on 2009-10-11
The easiest way to get the open-source 3D for r6xx in Karmic is to install your kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc3/)

and then add the following ppa to you software sources, run update-manager and reboot.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


edit:

Also independent of video driver there's a bug in Karmic that gives a corrupted tty,

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775)

removing 'splash' from the grub line fixed it for me.

---

### Post by Cerberus108 on 2009-10-12
> **monraaf said:**
> The easiest way to get the open-source 3D for r6xx in Karmic is to install your kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32-rc3/")

and then add the following ppa to you software sources, run update-manager and reboot.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")


It worked for me, although I'm using the ati driver instead of the radeonhd one. Got compiz and 3d enabled, everything smooth although not perfect (the blur is still not available).

---

### Post by Debianforce on 2009-10-12
Probably a stupid question, but will these drivers work on Asus Radeon HD 4850 cards?
The fglrx driver have never worked as intended on my PC or tv screen.

---

### Post by Yellow Pasque on 2009-10-12
They work on my 4550, at least in Jaunty, and apparently, they're now easy to install in Karmic (note that there was an update to the developmemnt kernel today [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc4/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc4/) ).

---

### Post by nistrum on 2009-10-15
I'm still on with this so I don't know what the results are going to be yet, fingers crossed. I thought I'd mention that building the kernel modules needed a bit of extra config for me since I've built my own kernel, namely:

```
LINUXDIR=/usr/src/linux make radeon.o drm.o
```

--Matt

---

### Post by nistrum on 2009-10-15
I'm having some trouble getting this going. I've done the other stuff and now I'm building mesa.

```
   -g -O2 -Wall -Wmissing-prototypes -std=c99 -ffast-math -fno-strict-aliasing  -fPIC  -DUSE_X86_64_ASM -D_GNU_SOURCE -DPTHREADS -DHAVE_POSIX_MEMALIGN -DUSE_EXTERNAL_DXTN_LIB=1 -DIN_DRI_DRIVER -DGLX_DIRECT_RENDERING -DGLX_INDIRECT_RENDERING -DHAVE_ALIAS -DHAVE_LIBDRM_RADEON=1 -I/usr/include/drm   -DRADEON_R600  radeon_screen.c -o radeon_screen.o
In file included from radeon_bocs_wrapper.h:8,
                 from radeon_common_context.h:20,
                 from radeon_common.h:4,
                 from radeon_screen.c:49:
/usr/include/drm/radeon_cs.h: In function ‘radeon_cs_set_limit’:
/usr/include/drm/radeon_cs.h:181: error: ‘RADEON_GEM_DOMAIN_VRAM’ undeclared (first use in this function)
/usr/include/drm/radeon_cs.h:181: error: (Each undeclared identifier is reported only once
/usr/include/drm/radeon_cs.h:181: error: for each function it appears in.)
radeon_screen.c: In function ‘radeonGetParam’:
radeon_screen.c:235: error: variable ‘info’ has initializer but incomplete type
radeon_screen.c:235: warning: excess elements in struct initializer
radeon_screen.c:235: warning: (near initialization for ‘info’)
radeon_screen.c:235: error: storage size of ‘info’ isn’t known
radeon_screen.c:240: error: ‘RADEON_PARAM_DEVICE_ID’ undeclared (first use in this function)
radeon_screen.c:241: error: ‘RADEON_INFO_DEVICE_ID’ undeclared (first use in this function)
radeon_screen.c:244: error: ‘RADEON_INFO_NUM_GB_PIPES’ undeclared (first use in this function)
radeon_screen.c:246: error: ‘RADEON_PARAM_NUM_Z_PIPES’ undeclared (first use in this function)
radeon_screen.c:247: error: ‘RADEON_INFO_NUM_Z_PIPES’ undeclared (first use in this function)
radeon_screen.c:252: error: ‘DRM_RADEON_INFO’ undeclared (first use in this function)
radeon_screen.c:235: warning: unused variable ‘info’
radeon_screen.c: In function ‘radeonCreateScreen’:
radeon_screen.c:1155: error: ‘RADEON_PARAM_NUM_Z_PIPES’ undeclared (first use in this function)
radeon_screen.c: In function ‘radeonCreateScreen2’:
radeon_screen.c:1299: error: ‘RADEON_PARAM_DEVICE_ID’ undeclared (first use in this function)
radeon_screen.c:1361: error: ‘RADEON_PARAM_NUM_Z_PIPES’ undeclared (first use in this function)
make[5]: *** [radeon_screen.o] Error 1

```

Any idea what might be causing it?

--Matt

---

### Post by n3had on 2009-12-28
> **monraaf said:**
> The easiest way to get the open-source 3D for r6xx in Karmic is to install your kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc3/)

and then add the following ppa to you software sources, run update-manager and reboot.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


edit:

Also independent of video driver there's a bug in Karmic that gives a corrupted tty,

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/447775)

removing 'splash' from the grub line fixed it for me.

what is your xorg?

I've updated the system using the packages drom the the ppa above and updated to kernel 2.6.32 and i can't enable compiz this is what i get

```
$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by tlinuxx on 2010-03-18
It's really weird! I freshly installed 10.04 Alpha3,the visual effect is amazing even without the AMD proprietary driver. I just want to check out what xorg.conf can make such a stunning desktop environment.But I was shocked that xorg.conf doesn't exist at all. Any UBUNTU guys know why?

---

### Post by Yellow Pasque on 2010-03-18
> **tlinuxx said:**
> It's really weird! I freshly installed 10.04 Alpha3,the visual effect is amazing even without the AMD proprietary driver. I just want to check out what xorg.conf can make such a stunning desktop environment.But I was shocked that xorg.conf doesn't exist at all. Any UBUNTU guys know why?
This thread is outdated in terms of Lucid. Lucid has the necessary pieces for basic 3D to work without any modification.

---

