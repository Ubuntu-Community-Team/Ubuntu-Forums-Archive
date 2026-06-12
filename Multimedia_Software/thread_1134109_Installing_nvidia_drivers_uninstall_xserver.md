---
title: "Installing nvidia drivers uninstall xserver"
date: 2009-04-23
forum: Multimedia Software
---

### Post by nawitus on 2009-04-23
If I attempt to install nvidia-glx-180, then apt-get wants to uninstall xserver itself. When I updated to 9.04 rc2, I had no problems. Then, after some updates I rebooted, and there was nvidia kernel mismatch. I reinstalled the nvidia-glx, which removed xserver. After that I installed xserver which removed nvidia-glx. 

> 
sudo apt-get install nvidia-glx-180
[sudo] password for nawi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms nvidia-180-kernel-source nvidia-180-libvdpau 
nvidia-settings
The following packages will be REMOVED:
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd 
xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-wacom 
xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark 
xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus 
xserver-xorg-video-fbdev
  xserver-xorg-video-geode xserver-xorg-video-i128 
xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 
xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-rendition 
xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx 
xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-v4l 
xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
The following NEW packages will be installed:
  dkms nvidia-180-kernel-source nvidia-180-libvdpau nvidia-glx-180
  nvidia-settings
0 upgraded, 5 newly installed, 40 to remove and 5 not upgraded.
Need to get 0B/14.4MB of archives.
After this operation, 28.6MB of additional disk space will be 
used.
Do you want to continue [Y/n]? 

The problem is described in launchpad but no responses there, it's supposedly fixed.
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/308410](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/308410)

---

### Post by cariboo on 2009-04-23
I would suggest that you haven't fully updated to Jaunty. Open a terminal and type:

```
sudo apt-get -f install
```

to install any missing dependencies, then run:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

to install any missing packages. Xorg-xserver is a newer version in Juanty, so if you haven't got the latest version installed you may run into problems.

---

### Post by nawitus on 2009-04-23
That did install a couple of packages (nothing xserver related, only firefox and xulrunner), but the problem persists.
EDIT: Problem solved, I just removed old 8.10 repositories from the list.

---

