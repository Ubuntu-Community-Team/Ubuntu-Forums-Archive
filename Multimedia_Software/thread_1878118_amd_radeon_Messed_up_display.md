---
title: "amd radeon Messed up display"
date: 2011-11-09
forum: Multimedia Software
---

### Post by ublinx on 2011-11-09
Hi All

I had been trying to install the latest AMD Radeon (11.9) Catalyst driver on my HP Probook4720s to try and get gnome shell to work. Unfortunately seems I messed up with my drivers as now I only get garbled image as soon as Ubuntu 11.10 is loaded (login screen). Can't get to a terminal session as well and the only way I can access my files is using a live cd.

I wanted to try and reinstall the amd drivers by booting the livecd but how to proceed to install it to the system on the drive and not the live one.

Can someone please help either by pointing to some guide or anything else.

Thanks

For info I'm running Ubuntu 11.10 - 64bit

---

### Post by ~!geek!~ on 2011-11-09
> **ublinx said:**
> Hi All

I had been trying to install the latest AMD Radeon (11.9) Catalyst driver on my HP Probook4720s to try and get gnome shell to work. Unfortunately seems I messed up with my drivers as now I only get garbled image as soon as Ubuntu 11.10 is loaded (login screen). Can't get to a terminal session as well and the only way I can access my files is using a live cd.

I wanted to try and reinstall the amd drivers by booting the livecd but how to proceed to install it to the system on the drive and not the live one.

Can someone please help either by pointing to some guide or anything else.

Thanks

For info I'm running Ubuntu 11.10 - 64bit

 And it happened to you too! Gnome-shell troubles! 
But are you not able to get to tty session.. by pressing ctrl+alt+f1 or f2 ... f6 at Login Screen. If you are then try removing it using one of these terminals..

---

### Post by ublinx on 2011-11-09
Hi ~!geek!~

That my problem. Even trying to get to a terminal session using CTRL+ALT+F key, screen is still garbled.
Only possibility is using a livecd, but then I can't chroot. (Actually i'm not even sure if chroot will help).

---

### Post by ublinx on 2011-11-09
Ok thanks everyone. Managed to get it working. For those interested, went through the recovery mode, enabling read and write access. Then reinstalled the ati driver that i had.
Booted back and seems to be working fine, both Unity and Gnome. :grin:

Thanks again for the help.

---

### Post by almursi on 2011-11-09
Hi, please note that Calalyst 11.10 is out days ago and seems to give better results both in natty as oneiric, but in any case is often the first attempt fails (usually, looking at the console, you see error information in the generation of symbolic links), so it is monitoring the issue and retry until you perform a clean installation errors. Regards,

---

### Post by ublinx on 2011-11-09
Hi Almursi, is it available on AMD website? Got only 11.9 over there? Or is it in a ppa/repository.

Thanks anyway for the info. Will look into it.

---

### Post by almursi on 2011-11-09
Hi, oops sorry :) [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by MoreOrLess on 2011-11-09
It's best to build .deb packages: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

---

### Post by almursi on 2011-11-09
> **MoreOrLess said:**
> It's best to build .deb packages...

Hi, yes, I was taking this by default, "and retry until you perform a clean installation errors" (on "dpkg -i *.deb" pass). Regards.

---

### Post by jmate24 on 2011-11-09
just use the one from the repos labeled fglrx-updates that will get you the latest fglrx and you will need to install this that i am attaching too. and you will need to go into the terminal and enter this:

```
sudo apt-get purge xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-radeon && sudo apt-get install prelink libevas1 libevas1-fb libevas1-engines-x libgl1-mesa-dri-experimental libogre-1.7.3 ogre-tools python-evas compiz compiz-core compiz-plugins libcegui-mk2-1 libegl1-mesa libfltk-gl1.3 libfltk-gl2 libghc-gtkglext-prof libghc-opengl-prof libgl2ps0 libglewmx1.6 libgtkgl2.0-1 libhugs-opengl-bundled libjngl0.9.5 libnux1.0-0 libosmesa6 libqt4-opengl libtogl1 libtulip-3.1 libtulip-ogl-3.1 nux-tools python-pyside.qt4opengl python-qt4-opengl x11proto-gl-dev drawxtl fglrx-updates fp-units-gfx-2.4.4 glew-utils gliv libcogl-common libcogl5 libcoin60 libcsfml-graphics libformsgl2 libfox-1.6-0 libghc6-opengl-prof libglc0 libglc2 libglee0d1 libgles1-mesa libgles2-mesa libglw1-mesa libgtkada-gl2.14.2 libgtkglextmm-x11-1.2-0 libguichan-0.8.1-1  libguichan-opengl-0.8.1-1 libopencascade-visualization-6.5.0 libopengl-perl libopengl-ruby libopengl-ruby1.8 libopengl-ruby1.9.1 libopengl-xscreensaver-perl libopenscenegraph80 libtiff-opengl mesa-utils-extra python-gtkglext1 python-pyglew python-soya rss-glx xscreensaver-gl xscreensaver-gl-extra unicode-screensaver xscreensaver-data-extra dkms
```

then run in a terminal:

```
sudo prelink -v -a -f
```

then reboot.

---

