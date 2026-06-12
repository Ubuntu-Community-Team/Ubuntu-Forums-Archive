---
title: "nVidia 100.14.11 via envy and dev package?"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by jboehm on 2007-09-12
Hi,

I'm running fiesty fawn.  I want to get the latest nvidia drivers, 100.14.11.  The easiest way I have heard is to used envy.  I've used it in the past and its great.  The only problem I'm anticipating is that I need the nvidia-glx-new-dev package for programs I compile myself.  The currently installed nvidia-glx-new-dev is for the nvidia-glx-new package in the repository which is for 1.0.9755.  

How do I get a nvidia-glx-new-dev for 100.14.11?  Is this even something that will cause a problem?

Thanks,
Jon

---

### Post by dabl on 2007-09-12
Can't you just install the nvidia-glx-new package, and get the 100.14.11 driver that way?  It hasn't had the -9755 driver in it for a month or more.

---

### Post by jboehm on 2007-09-12
> **dabl said:**
> Can't you just install the nvidia-glx-new package, and get the 100.14.11 driver that way?  It hasn't had the -9755 driver in it for a month or more.


What???  My box is up-to-date.  I've done recent apt-get updates and upgrades. Note the version number below for the apt-cache show is 1.0.9755.  Whats going on????


me@mybox:~$ apt-cache show nvidia-glx-new
Package: nvidia-glx-new
Priority: optional
Section: restricted/misc
Installed-Size: 14400
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20 (2.6.20.5-16.29)
Version: 1.0.9755+2.6.20.5-16.29
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video
Depends: nvidia-kernel-1.0.9755, linux-restricted-modules-common, xserver-xorg-core (>= 1:0.99.0-1), libglu1-mesa | libglu1, libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libgl1-mesa | libgl1, libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.16.2), libx11-6, libxext6, nvidia-glx
Suggests: nvidia-settings, nvidia-new-kernel-source (>= 1.0.9755)
Conflicts: nvidia-glx-src, nvidia-glx, nvidia-glx-legacy
Filename: pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-16.29_i386.deb
Size: 4833116
MD5sum: 95f66ffbcbf6808cf80b5b242ac31063
SHA1: 4a5291bdd5b7b12d33090f82b046f1aff83559ec
SHA256: cb0bf5d47e605e490798f781c0aef7a16837341698913ba6fce51fc4737cc5b3
Description: NVIDIA binary XFree86 4.x/X.Org 'new' driver
 These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
 of OpenGL applications via a direct-rendering X Server and supports the  newer
 GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
 flat panel displays are also supported.
 .
 If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
 package instead of this one. If you have a GeForce4, you may need the nvidia-glx
 package.
 .
 To enable the driver, run "sudo nvidia-glx-config enable".
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: nvidia-glx-new
Priority: optional
Section: restricted/misc
Installed-Size: 14400
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-restricted-modules-2.6.20 (2.6.20.5-15.20)
Version: 1.0.9755+2.6.20.5-15.20
Replaces: nvidia-glx-src
Provides: nvidia-glx, xserver-xorg-video
Depends: nvidia-kernel-1.0.9755, linux-restricted-modules-common, xserver-xorg-core (>= 1:0.99.0-1), libglu1-mesa | libglu1, libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libgl1-mesa | libgl1, libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.16.2), libx11-6, libxext6, nvidia-glx
Suggests: nvidia-settings, nvidia-new-kernel-source (>= 1.0.9755)
Conflicts: nvidia-glx-src, nvidia-glx, nvidia-glx-legacy
Filename: pool/restricted/l/linux-restricted-modules-2.6.20/nvidia-glx-new_1.0.9755+2.6.20.5-15.20_i386.deb
Size: 4832942
MD5sum: b609e79ad5f7b37d78dcac227804c0bd
SHA1: 4d56c49c9d9d342dbce749974a25012d476c330f
SHA256: 7a6902f17467b9342c66d006c54a9215759e19cd3c61fccf30a48e5ccd0677d4
Description: NVIDIA binary XFree86 4.x/X.Org 'new' driver
 These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
 of OpenGL applications via a direct-rendering X Server and supports the  newer
 GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
 flat panel displays are also supported.
 .
 If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
 package instead of this one. If you have a GeForce4, you may need the nvidia-glx
 package.
 .
 To enable the driver, run "sudo nvidia-glx-config enable".
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by jboehm on 2007-09-12
> **dabl said:**
> Can't you just install the nvidia-glx-new package, and get the 100.14.11 driver that way?  It hasn't had the -9755 driver in it for a month or more.

Are you sure your not thinking of gusty?  Fiesty, I'm almost positive is still at -9755

[http://packages.ubuntu.com/feisty/misc/nvidia-glx-new](http://packages.ubuntu.com/feisty/misc/nvidia-glx-new)    Fiesty 9755
[http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new)    Gusty 100.14.11

---

### Post by dabl on 2007-09-12
No, I'm also running Feisty 64-bit Ubuntu, and Envy installed the 100.14.11 driver there, even before they put it in the nvidia-glx-new package.  Why don't try removing that package (you may need to configure a VESA display for 15 minutes) and then re-install it?  It was in July that they put 100.14.11 into the nvidia-glx-new package.

---

### Post by jboehm on 2007-09-13
> **dabl said:**
>   It was in July that they put 100.14.11 into the nvidia-glx-new package.

That doesn't make any sense to me.  Do you have backports enabled in your source.list possibly? On two different FF boxes I see synaptic stating that the latest version of glx-new is 1.0.9755.

Thanks,
Jon

---

### Post by jboehm on 2007-09-14
bump

---

