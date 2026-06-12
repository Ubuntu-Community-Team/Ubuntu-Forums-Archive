---
title: "mesa instead of fglrx! :("
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by Dimas on 2006-07-04
My problem:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

It happened when I updated ati drivers from saveas repository I think. Or when I updated the mesa libraries... I don't know :(

I think there's something wrong here:

```
$ ls -alis /usr/lib/fglrx/
total 452
390818   4 drwxr-xr-x   2 root root   4096 2006-07-04 20:31 .
340038  40 drwxr-xr-x 164 root root  40960 2006-07-04 20:31 ..
388609 408 -rw-r--r--   1 root root 410880 2006-06-28 21:21 libGL.so.1.2.xlibmesa
388610   0 lrwxrwxrwx   1 root root     12 2006-07-03 22:20 libGL.so.1.xlibmesa -> libGL.so.1.2
```

```
$ ls -alis /usr/lib/ | grep libGL
341234     0 lrwxrwxrwx   1 root root       16 2006-06-02 19:08 libGLEW.so.1.3 -> libGLEW.so.1.3.1
341235   208 -rw-r--r--   1 root root   205204 2005-11-30 21:47 libGLEW.so.1.3.1
340409     0 lrwxrwxrwx   1 root root       12 2006-07-03 22:21 libGL.so.1 -> libGL.so.1.2
340404   632 -rwxr-xr-x   1 root root   642476 2006-06-26 21:48 libGL.so.1.2
342733     0 lrwxrwxrwx   1 root root       20 2006-07-03 22:21 libGLU.so.1 -> libGLU.so.1.3.060500
342720   476 -rw-r--r--   1 root root   483308 2006-06-28 21:21 libGLU.so.1.3.060500
```

Anyone can help? Thx!

Update: I've already readed the "HOWTO: Fixing the Mesa Issue for ATI Cards" post, and not helped me :|

---

### Post by Dimas on 2006-07-04
Viewing /var/log/Xorg.0.log I think I've found the problem:

```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.25.18
(II) fglrx(0):     Date: May 18 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb71e6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

I have ATI property version 8.26, not 8.25. What can I do?

---

### Post by inktaylor on 2006-07-04
ati appears to have previous drivers available if you look under linux and your card at the list on the grey side panel here:  [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

### Post by Dimas on 2006-07-05
[QUOTE=inktaylor]ati appears to have previous drivers available if you look under linux and your card at the list on the grey side panel here:  [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)[/QUOTE]

Yes, If I downgrade to 8.25 goes fine, but if 8.26 goes to other poeple why not to me? :/

---

### Post by james016 on 2006-07-05
I'm getting the same thing.

---

### Post by Dimas on 2006-07-05
I view two posible causes:

**1) Kernel fglrx Module is 8.25, and the driver I've installed is the 8.26.**
(*(WW) fglrx(0): Kernel Module version does *not* match driver.*)
I tried:
- If I downgrade to 8.25 driver all goes fine. But when I update to 8.26 it doesn't match with kernel module version and I don't have acceleration.
- I tried to disable kernel fglrx module, but when I reboot I don't have acceleration.
Solution?
- Downgrade to 8.25 driver.. but for xgl sux.
- Update kernel fglrx module to 8.26. _BOT HOW??_ :(

**2) Driver is compiled for x.org 6.8.99.8 but I've 7.0**
If that's the problem, Why other people with dapper can run 8.26 drivers? :/

Can anyone help with **1)** ?

---

### Post by whatever on 2006-07-05
[QUOTE=Dimas]- Update kernel fglrx module to 8.26. _BOT HOW??_ :([/QUOTE]
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually)

---

### Post by Dimas on 2006-07-05
Thx whatever, but the problem continue :/

Did you know if are correct these sections of my xorg.conf correct for 8.26 property drivers and ati 9700 ? I tried to enable/disable *Load "dri"* but the *[drm] failed to load kernel module "fglrx"* is there...

```
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "DRI"
	Mode         0666
EndSection
```

Looks like the problem is DRI:

```
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

---

### Post by whatever on 2006-07-06
did you actually build the new module or did you just blacklist the old one? :rolleyes:

---

### Post by Dimas on 2006-07-06
[QUOTE=whatever]did you actually build the new module or did you just blacklist the old one? :rolleyes:[/QUOTE]

Uhm??

I disabled fglrx module in kernel-restricted-modules-common and followed [this]("http://ubuntuforums.org/showthread.php?t=204910") steps. I'm wrong in something?

---

