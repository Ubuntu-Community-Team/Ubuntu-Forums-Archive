---
title: "Has anyone got Nouveau Gallium 3D drivers working for nvidia cards?"
date: 2009-12-05
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-12-05
Hi,

I read that Ubuntu 10.04 is going to include Nouveau Gallium 3D drivers by default for nvidia cards.

I want to try out the Nouveau Gallium 3D drivers on Ubuntu 9.10.  The Nouveau web site only seams to have instructions for installing the 2D drivers on Ubuntu as the 3D ones are unstable.  I found this link: [http://ubuntuforums.org/showthread.php?t=1046504&page=2]("http://ubuntuforums.org/showthread.php?t=1046504&page=2")

The 3rd last post says 3D support has been moved to a separate kernel branch.

How do I install Gallium 3D drivers for my nvidia card?

I know how to compile software from source it is easy.  Just download it with either svn or git clone and then cd to the directory and type make, sudo make install (sometimes you need ./Configure too).  But I have no idea how to rebuild my kernel!!!  I have tried following guides on how to do it.  But am totally lost!

---

### Post by HappyFeet on 2009-12-06
Just do
```
sudo apt-get install xserver-xorg-video-nouveau
```
and reboot.

---

### Post by Captain_Glen on 2009-12-06
Thanks

That plus editing /etc/X11/xorg.conf to:

```
Section "Device"
    Identifier "Device0"
    Driver "nouveau"
```

Fixed it.

But I am having trouble configuring Dualhead/twinview.  Is there a GUI program I can use to set which is the primary display?  I use to use nvidia-settings when I was using proprietary drivers.

Also my 3D doesn't work properly.  I can get 3D if I load up the Tux Snow racing game.  But it doesn't draw it on one screen and I can't select anything.  Also compiz doesn't work.

I guess that the drivers aren't mature enough yet.  If I build the drivers from source will compiz work?

Any help would be appreciated.

---

### Post by Charlie708 on 2009-12-19
I've used the Nouveau 3D driver, but only under Gentoo.  It requires Mesa 7.6 to be built with Gallium3D components, and its HIGHLY experimental.

With 3D, glxgears work, compiz works (but can act up), but not much else works.  Also, the performance is pretty low.  If you need 3D, you need to stick with the blob for now.

---

