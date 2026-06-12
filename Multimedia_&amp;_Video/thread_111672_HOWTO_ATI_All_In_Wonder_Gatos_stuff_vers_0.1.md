---
title: "HOWTO: ATI All In Wonder Gatos stuff vers 0.1"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by markuman on 2006-01-02
original in german: [http://wiki.ubuntuusers.de/ATI/AIW](http://wiki.ubuntuusers.de/ATI/AIW)
source: [http://gatos.sf.net](http://gatos.sf.net)

[i]Version 0.1
1. about
2. Install ati.2 Drivers &#8211; for watching tv
3. KM-Modul &#8211; Linux kernel module that provides Video4linux capture interface for ATI video cards capable of video capture[/i]



**1. about**

in the ubuntu repos we find a package called &#8222;gatos&#8220;.
this package does not require kernel patches, and includes: 
  ```
* xatitv: GUI TV-in-a-window application
       GUI access to all GATOS functionality, save tv-out.
  * atitv: Simple text-mode program
       Basic functionality to record video and toggle tv-out.
  * atitoppm:
  * atitogif:
  * atitojpg:
       YUV conversion utilities
  * yuvsum: video field to frame converter
       Averages all images in gatos.yuv (must all
       be same size).
  * atisplit: YUV conversion to ucbmpeg
       This splits the output file for MPEG encoding.
 This software is not intended to support most recent ATI AIW Radeon
```
so we need the km-module and from gatos the ati.2 driver.

latest ati.2 driver is for Xorg6.7 - don&#180;t work for me on breezy!
so have to wait for dapper with Xorg7 (perhaps?) or update yourself to xorg7. because gatos ati.2 drivers are inculded in xorg7

**Note: Without the gatos ati.2 driver is the km module useless!**

for watching tv it should be enough to use the "radeon" (ati.2) driver from gatos.





**2. Install ati.2 Drivers** &#8211; *for watching tv*


ATI-6.7.0-exp1.i386.tar.gz &#8211; *could be tried in hoary and breezy.*

for warty: ati.2: XFree86 4.3.0 driver

both from: [http://sourceforge.net/project/showfiles.php?group_id=12629](http://sourceforge.net/project/showfiles.php?group_id=12629)

    * Backup your /usr/X11R6/ 
    * Make sure that /usr/X11R6 
    * Change directory to /usr and unpack the archive:
 ```
sudo tar zxvf ATI-6.7.0-exp1.i386.tar.gz
```

      This will install some additional modules and replace some binaries that are part of standard XFree86 4.3.0/Xorg6.8 installation.
    * Choose "radeon" drivers (or try "ati" - who knows?) in your xconfig.
    * Restart X server if it was running. 
If X runs &#8211; Congratulations! 
If not, restore your backup from /usr/X11R6/ - Upgrate to Xorg7 ! *wanted!!*



**3. KM-Modul** &#8211; *Linux kernel module that provides Video4linux capture interface for ATI video cards capable of video capture*
we need somthing for compiling and the kernel-source.
```
sudo aptitude install build-essential linux-headers-$(uname -r) 
```
 get the KM Source from sf.net
[http://sourceforge.net/project/showfiles.php?group_id=12629&package_id=30029&release_id=336707](http://sourceforge.net/project/showfiles.php?group_id=12629&package_id=30029&release_id=336707) 
extract the archiv and enter it.
```
mv Makefile-2.6 Makefile
sudo make -C /usr/src/linux-headers-$(uname -r) SUBDIRS=$PWD modules
```

if there were no errors we&#180;ve got 2 kernel modules.
now we have to put them only on the right place.
```
sudo cp km_api_drv.ko /lib/modules/2.6.xxx/kernel/drivers/video
sudo cp km_drv.ko /lib/modules/2.6.xxx/kernel/drivers/video
```
lets check if it works... 
```
sudo modprobe videodev
sudo modprobe km_drv
```
if there were no notes or errors we can add the following lines in the /etc/modules
```

videodev
options km_drv km_debug=0
km_drv
```

---

to be continued...
any feedback? any experience with xorg7?
*comming next: drm module?; gatos tv out; update xorg7;...*

---

### Post by auburn on 2006-03-28
Markuman, I'm dying here to hear more about "gatos tv out". Did you ever get into that? I have an AIW 7500. Thx

---

