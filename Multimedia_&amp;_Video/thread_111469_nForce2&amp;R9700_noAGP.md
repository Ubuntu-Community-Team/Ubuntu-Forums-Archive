---
title: "nForce2&amp;R9700 noAGP"
date: 2006-01-02
forum: Multimedia &amp; Video
---

### Post by La_Frenezo on 2006-01-02
System:
Mainboard: ASUS nForce2 400
GPU: Radeon 9700 AGP
CPU: Athlon XP 2500+

When I try to install the ATI driver over Automatix it kills my X11, and when I try to install it manual or by the ATI 50MB "auto-installer" I just get the control panel with no hardware acceleration. That made me to think that my AGP-port gets used as PCI or something. The device-manager shows that too (as you can see on my added screenshot):

Can anybody help me? Thanks for reading!

---

### Post by Amon_Re on 2006-01-02
[QUOTE=La_Frenezo]System:
Mainboard: ASUS nForce2 400
GPU: Radeon 9700 AGP
CPU: Athlon XP 2500+

When I try to install the ATI driver over Automatix it kills my X11, and when I try to install it manual or by the ATI 50MB "auto-installer" I just get the control panel with no hardware acceleration. That made me to think that my AGP-port gets used as PCI or something. The device-manager shows that too (as you can see on my added screenshot):

Can anybody help me? Thanks for reading![/QUOTE]

Device manager always shows AGP cards as "PCI", that's not the root of your problem. You say it kills your X11, how so? As for ATI's autoinstaller, there's a howto somewhere on the forums with the proper installation guide.

Start with the basics, do the following

dmesg | grep "agp"
dmesg | grep "fglrx"
grep "agp" /var/log/Xorg.0.log
grep "fglrx" /var/log/Xorg.0.log

And post the output

---

### Post by La_Frenezo on 2006-01-02
Okay, some commands:

dmesg | grep "agp"
[4294696.022000] Linux agpgart interface v0.101 (c) Dave Jones
[4294696.031000] agpgart: Detected NVIDIA nForce2 chipset
[4294696.039000] agpgart: AGP aperture is 64M @ 0xe0000000

fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

glgears and ATI controlpanel also complain about the missing "XFree86-DRI"-extension

If I use this commands:
dmesg | grep "fglrx"
grep "agp" /var/log/Xorg.0.log
grep "fglrx" /var/log/Xorg.0.log
->I get no output.

I already tried this ways to install the driver:
ATI-driver with ubuntuguide -> missing acceleration
ATI-autoinstaller -> missing acceleration
ATI-driver by AUTOMATIX -> dead X11

I'm going to try it another time by some guide in a Ubuntuforum. Thanks for your reply!

---

### Post by La_Frenezo on 2006-01-02
Ok, tried another method. Controlpanel is completely working now, but it shows "PCI-transfermode". Also glxgears runs slowly as hell.

Here is a lil extract of the grep "fglrx" /var/log/Xorg.0.log

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled

---

