---
title: "VDPAU not working?"
date: 2011-09-07
forum: Multimedia Software
---

### Post by Anoobis on 2011-09-07
I've got an Acer Revo here with the Nvidia Ion graphics etc but despite everyone going on about how good HD video is on these things mine doesn't even want to consider anything above 640x480. It just freezes for 10 seconds at a time.
While doing the standard updating this came up, I'm guessing its related but i've no idea where to go with it.

```
Setting up nvidia-current (280.13-0ubuntu1~natty~xup1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/nvidia-current/ld.so.conf because link group gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-280.13 DKMS files...
Building only for 2.6.38-11-generic
Building for architecture i686
Building initial module for 2.6.38-11-generic
Done.

```

---

### Post by papibe on 2011-09-07
It seems that you are running Natty.

Did you install the Nvidia driver from 'Additional drivers' or from the Nvidia site?

Could you post your /etc/X11/xorg.conf?

Also, could you post the result of this command?
```
$ apt-cache policy libvdpau1
```
Regards.

---

### Post by Anoobis on 2011-09-08
Yes running natty - not 10.04 as the sidebar says!
xorg.conf:
```
Section "Screen"

	Identifier	"Default Screen"

	DefaultDepth	24

EndSection


Section "Module"

	Load	"glx"

EndSection



Section "Device"

	Identifier	"Default Device"

	Driver	"nvidia"

	Option	"NoLogo"	"True"

EndSection
```

and result of apt-cache policy libvdpau1 :
```
libvdpau1:

  Installed: 0.4.1-2ubuntu1

  Candidate: 0.4.1-2ubuntu1

  Version table:

 *** 0.4.1-2ubuntu1 0

        500 http://gb.archive.ubuntu.com/ubuntu/ natty/main i386 Packages

        100 /var/lib/dpkg/status

W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ natty/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages)

W: You may want to run apt-get update to correct these problems
```
apt-get update doesn't get me anywhere with this.

Is this any help?

---

### Post by papibe on 2011-09-08
Could you post your /etc/apt/sources.list ?

Regards.

---

### Post by drawkcab on 2011-09-09
Make sure you have ffmpeg installed:

[http://ubuntuforums.org/showthread.php?t=786095&highlight=howto+ffmpeg](http://ubuntuforums.org/showthread.php?t=786095&highlight=howto+ffmpeg)

Make sure you're using SMplayer with vdpau enabled in the options.

---

