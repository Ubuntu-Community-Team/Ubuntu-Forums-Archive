---
title: "[SOLVED] ATI X300 - cannot install the driver"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by mah01 on 2007-11-30
Hi.

I knows guys - you are bored from this kind of posts, but I'm already sick of unsuccessful configuring my video card driver. Ubuntu is really hard because of small problems (used Ubuntu on my dell laptop already). These problems can be solved through ubuntuforums.org, but every time too much effort required. Because of that, I'm thinking about creating community causeWindowsIsBetter.com. I already know my PR program. Please, guys, don't let me do that..

Ok, problem is - I cannot configure my ATI X300 driver. I simply want resolution 1280x1024. 3 days I was trying to do it on my own searching through the forum and trying various solutions. Neither helped. I've reinstalled Ubuntu three times already, to begin from scratch. I'm trying that with Ubuntu 7.10.

I've found beautiful howto here:
[http://ubuntuforums.org/showthread.php?t=575843&highlight=ati+for+dummies](http://ubuntuforums.org/showthread.php?t=575843&highlight=ati+for+dummies)
which redirect the reader here:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

Ok, I'm showing you my installation steps that I'm trying.

**************************************************************************
**[SIZE="3"]Ubuntu Gutsy Installation Guide[/SIZE]**

> Enable "restricted" Repository

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

System > Administration > Software Sources. Check "Proprietary Drivers for Devices (Restricted)" box. 
I'm providing:
```
sudo gedit /etc/apt/sources.list
```
and uncommenting:
```
deb http://lt.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://lt.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```
Saving file.

Trying **Method 1**:
> ```
sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```
Everything seems to be ok. Rebooting.
Em.. Nothing changed. Trying **Method2**.

> Download the ATI driver installer: ati-driver-installer-7-11-x86.x86_64.run (this installer is for 32bit and 64bit systems)
Downloaded
> Install necessary tools:
```

sudo apt-get update
sudo apt-get install module-assistant build-essential fakeroot dh-make debhelper \
debconf libstdc++5 linux-headers-generic
```

ok
> Create .deb packages:

```
sudo bash ati-driver-installer-7-11-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

Ok, installed.
> Blacklist old fglrx module from linux-restricted-modules:
Ubuntu/Gnome users type in:

```
gksu gedit /etc/default/linux-restricted-modules-common
```
```
DISABLED_MODULES="fglrx"
```

Done.
> Install .deb packages:

```
sudo dpkg -i xorg-driver-fglrx_8.433-1*.deb fglrx-kernel-source_8.433-1*.deb fglrx-amdcccle_8.433-1*.deb
```

Done.
Skipping few steps, because I don't have 64-bit architecture and I don't have any older fglrx versions installed.
> ```
sudo gedit /etc/init.d/ati-module-fix
```
And put this in it:

```
#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0

```
Make it executable

```
sudo chmod ugo+x /etc/init.d/ati-module-fix
```
Now, make this run before gdm (which starts with sequence number 13)

```
sudo update-rc.d ati-module-fix defaults 12
```


Done all the steps. Checking gdm sequence number:
```
ls /etc/rc2.d/
```
receiving:
```
 S30gdm
```
Because of that making ati-module-fix sequence 29:
```
sudo update-rc.d ati-module-fix defaults 29
```
> Comment the following line in the file /etc/modprobe.d/lrm-video { add at 27/11/2007 }

```
# Make nvidia/nvidia_legacy and fglrx use /sbin/lrm-video to load
#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS #  << this line
install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS
install nvidia_legacy /sbin/lrm-video nvidia_legacy $CMDLINE_OPTS
install nvidia_new /sbin/lrm-video nvidia_new $CMDLINE_OPTS
```

Alright, uncommented. Now, rebooting.
> ```
sudo aticonfig --initial
```

Then:

```
sudo aticonfig --overlay-type=Xv
```
```
sudo shutdown -hr now
```

Entering asked commands and rebooting.
**Perfect** My resolution changed. Now it's 1600x1200. My SyncMaster 770p started to complain that it should be 1280x1024 60mhz. Ok, no problem, changing.
Cool, It's working. It's really working!
Checking with fglrxinfo:
```
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```
Howto says, Mesa is bad, but I actually don't care why it's bad. 
Restarting the machine just to test, if resolution remains normal.
After restart I get "Ubuntu is running in low-graphic mode" and resolutions is set to 800x600!!
Why?
checking "fglrxinfo":
```
~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

```
Please, suggest me something

---

### Post by mah01 on 2007-11-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
actually returned first installation of Ubuntu. It's written that it's 1280x1024, but it's like streched a bit vertically and it's seems like it's 1280x960 or smth

---

### Post by mah01 on 2007-11-30
Just enabled in "Restricted Driver Manager" ATI graphic driver and resolution went to normal. After rebooting resolution remained normal.
cool.

---

