---
title: "AMD Video Driver Headaches"
date: 2011-12-23
forum: Multimedia Software
---

### Post by jim_deadlock on 2011-12-23
My dad has an AMD RadeonHD 6450. From a fresh Ubuntu install I've found the only way to get a desktop environment is by booting into recovery shell, removing the fglrx stuff and then installing the proprietary driver from the AMD site.

```
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo dpkg-reconfigure xserver-xorg
sudo ./ati-driver-installer-11-11-x86.x86_64.run
```

My problem is that 3D support seems to be disabled, the system will only log me into a Unity 2D environment and I can't get my compiz cube running. Also, I get horizontal flickering lines when viewing a video or moving windows around. I suspect that I need to reinstall fglrx, but the last time I tried to install fglrx-amdcccle it broke my desktop and I ended up having to do a fresh system install, so now I'm very wary.

```
# /usr/lib/nux/unity_support_test
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  22
  Current serial number in output stream:  22
```

```
# sudo apt-get install fglrx fglrx-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 fglrx : Recommends: fglrx-amdcccle but it is not going to be installed
         Conflicts: fglrx-driver
 fglrx-updates : Conflicts: fglrx-driver
E: Unable to correct problems, you have held broken packages.
# sudo apt-get remove fglrx-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'fglrx-driver' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by inobe on 2011-12-23
i can't really help you with manual installation.

but as you can see below, it looks like those packages need to be purged before updating.

```
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 fglrx : Recommends: fglrx-amdcccle but it is not going to be installed
         Conflicts: fglrx-driver
```

in any case, i would try the easy ways first, x-swat ppa is the best bet, but to use it, you will need to cleanup first, i wouldn't know where to begin.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

i use the ppa to update my nvidia driver.

---

### Post by jim_deadlock on 2011-12-23
As you can see above, I already tried to remove fglrx-driver but it wouldn't let me.

If my dad had an nVidia card like you and me then I wouldn't be having any of these problems...

---

### Post by SnickerSnack on 2011-12-23
I have a Radeon HD 6850 that I installed about a week ago.  Have you tried the 'additional drivers' tool in the main menu?  It doesn't give the newest driver, but it may work.  The 'update' to the driver seems to not want to install.

Also, the 6450 is on the list of supported cards, but do you meet these conditions:

```
The following hardware is supported by current releases of the Catalyst/fglrx driver. Open source drivers will work as well. Note that RadeonHD 6xx0 chips will need kernel 2.6.38 for open-source mode-setting, xf86-video-ati/radeon 6.14.0 for 2D acceleration (EXA/Xv), and Mesa 7.11 for 3D acceleration.
```

From: [Http://wiki.cchtml.com/index.php/Hardware#Not_Yet_Supported_or_Unoffically_Supported](Http://wiki.cchtml.com/index.php/Hardware#Not_Yet_Supported_or_Unoffically_Supported)

---

### Post by QIII on 2011-12-23
The ATI driver install "broke" your desktop because there is a step that is not well known.

Go through the drill of removing and purging the ATI driver again and making sure you have the open source Radeon driver.

You can get some help here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Boot back up and you should be able to get your desktop stable with the open source driver it will default to.

Install the ATI driver (fglrx and amdcccle) from Synaptic.  Synaptic should pick up the dependencies.

When the driver is installed, do NOT shut down.  You need to do the step that is not well known.

Use the terminal and run

```
sudo aticonfig --initial
```This will set up a basic xorg.conf for you (which does not exist by default in Ubuntu any longer and is why your DE broke).  You should then be able to use amdcccle (the Catalyst Control Center) to further configure the driver.  3D and all.

(Actually, if you had run that command the first time you were left at the command prompt without getting to your DE, you'd have been able to reboot and get in just fine.)

I have used ATI cards since the bad old days before AMD purchased ATI.  They work fine, but this little tidbit is just not well publicized.

Well, the drivers work fine in Ubuntu.  When running KDE 4.7 on Fedora 16, the ATI driver will wreak all sorts of havoc.

---

### Post by jim_deadlock on 2011-12-23
QIII, thanks for the info, I followed your instructions (output below) but I now have a new problem. After rebooting the desktop looks fine and it seems that 3D support is enabled, but unfortunately this only lasts for 5-10 seconds before the screen freezes, mouse and all, and needs a hard reboot. I've tried rebooting a few times but it always freezes. Any further advice?

```
# sudo ./ati-driver-installer-11-11-x86.x86_64.run --uninstall
restore of system environment completed
Uninstall fglrx driver complete.
For detailed log of uninstall, please see /etc/ati/fglrx-uninstall.log
System must be rebooted to avoid system instability and potential data loss.
# sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot fglrx-amdcccle patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed
  dkms fakeroot fglrx fglrx-amdcccle patch
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 42.1 MB of archives.
After this operation, 131 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main patch amd64 2.6.1-2 [80.7 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main dkms all 2.2.0.2-1ubuntu4 [72.3 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ oneiric/main fakeroot amd64 1.17-1 [107 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates/restricted fglrx amd64 2:8.881-0ubuntu4.1 [36.2 MB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates/restricted fglrx-amdcccle amd64 2:8.881-0ubuntu4.1 [5,628 kB]
Fetched 42.1 MB in 23s (1,816 kB/s)                                            
Selecting previously deselected package patch.
(Reading database ... 161151 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_amd64.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_amd64.deb) ...
Selecting previously deselected package fglrx.
Unpacking fglrx (from .../fglrx_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.881-0ubuntu4.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up fglrx (2:8.881-0ubuntu4.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.881 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-14-generic
Building for architecture x86_64
Building initial module for 3.0.0-14-generic
Done.

fglrx:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-14-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up fglrx-amdcccle (2:8.881-0ubuntu4.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
# sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-1
# 

```

---

### Post by jim_deadlock on 2011-12-24
Well, I once again purged everything and reinstalled the proprietary driver, but this time I used your magic command and now I have a stable (so far) 3D desktop. It would be nice to have the open source drivers if I could get them working, but for now I have a stable 3D desktop so I'm going to stop messing around with it... at least for a while. In the meantime I'm considering getting a tattoo of that magic command so I never forget it :biggrin:

Thanks very much QIII

---

