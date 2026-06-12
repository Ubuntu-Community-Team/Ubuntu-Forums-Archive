---
title: "Problem with libdrm and dpkg-shlibdeps"
date: 2008-10-28
forum: Multimedia Software
---

### Post by metanoya on 2008-10-28
Hi people.

I recently bought myself a 19" lcd flat screen and want to hook it up to my laptop to go dual screen.  I have an intel GM965 and Ubuntu 8.04.  I found this tutorial which looks quite helpful:

[http://ebsteblog.wordpress.com/2008/08/27/dual-head-on-ubuntu-hardy-with-intel-gm965-part-1/](http://ebsteblog.wordpress.com/2008/08/27/dual-head-on-ubuntu-hardy-with-intel-gm965-part-1/)

When I'm trying to build the intel driver, I get the following error and warnings:

dpkg-shlibdeps: warning: symbol xf86ModesEqual used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86SetScrnInfoModes used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol RRCrtcGammaSet used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol DamageDestroy used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol DamageDamageRegion used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86DeallocateGARTMemory used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol vgaHWMapMem used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CProbeAddress used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol vgaHWHBlankKGA used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol FreeScratchPixmapHeader used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/intel_drv.so found in none of the libraries.
dpkg-shlibdeps: warning: 266 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: symbol xf86I2CReadByte used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86DrvMsg used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CDevInit used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Xfree used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Xcalloc used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CWriteByte used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol ErrorF used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/ch7xxx.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CReadByte used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/tfp410.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86DrvMsg used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/tfp410.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CDevInit used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/tfp410.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Xfree used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/tfp410.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Xcalloc used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/tfp410.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CWriteByte used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/tfp410.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CReadByte used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/sil164.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86DrvMsg used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/sil164.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CDevInit used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/sil164.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Xfree used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/sil164.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol Xcalloc used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/sil164.so found in none of the libraries.
dpkg-shlibdeps: warning: symbol xf86I2CWriteByte used by debian/xserver-xorg-video-intel/usr/lib/xorg/modules/drivers/sil164.so found in none of the libraries.
dpkg-shlibdeps: failure: no dependency information found for /lib/libdrm.so.2 (used by debian/xserver-xorg-video-intel/usr/lib/libI810XvMC.so.1.0.0).
dh_shlibdeps: command returned error code 512

Can anybody please tell me what this means and how to fix this?

Thank you very much.

---

### Post by metanoya on 2008-10-30
Hi

I finally got dual screen to work.

I would just like to know how to make my laptop screen (LVDS) the default?

I added the virtual part to Screen in xorg.conf.  I then used:

xrandr --output VGA --auto
xrandr --output VGA --right-of LVDS

This works, but the taskbar and panel is now on VGA.  Also, when I open a new program, it opens up on VGA.  I would like it to open up on LVDS.

So, can anyone please advise me on how to do this?

Thank you very much.

---

