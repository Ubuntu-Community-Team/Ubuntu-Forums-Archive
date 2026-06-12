---
title: "Any updates/installs break nvidia-current"
date: 2010-12-20
forum: Multimedia Software
---

### Post by mizokia on 2010-12-20
This is a problem I've put up with for a while, but would like to solve. Any time I install the recommended updates, or even when I manually install a program myself, my nvidia-current stops working. Here is an example of the errors I got while installing Apache2. I'm not even sure why installing Apache2 has anything to do with my video card drivers.

> Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-current/ld.so.conf because link group gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib/libvdpau_nvidia.so because associated file /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib/xorg/modules/drivers/nvidia_drv.so because associated file /usr/lib/nvidia-current/xorg/nvidia_drv.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.24 DKMS files... 
------------------------------
Deleting module version: 195.36.24
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-195.36.24 DKMS files...
Building only for 2.6.32-25-generic
Building for architecture x86_64
Building initial module for 2.6.32-25-generic

Error! Application of patch vga_arbiter_workaround.patch failed.
Check /var/lib/dkms/nvidia-current/195.36.24/build/ for more information.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 6

Once I restart, my graphics are broken. I have to exit into login console, then find my Nvidia .run and sudo sh it. This makes it work again, until the next upgrade/install. Has anyone come across this before?

---

