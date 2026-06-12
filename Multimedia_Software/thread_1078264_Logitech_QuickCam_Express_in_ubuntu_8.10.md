---
title: "Logitech QuickCam Express in ubuntu 8.10"
date: 2009-02-23
forum: Multimedia Software
---

### Post by trickysnake on 2009-02-23
Hello!
I have some problem and I hope that you can suggest me something

I cant do work my camera Logitech QuickCam Express in ubuntu 8.10

From the beginning lsusb showed this:

Bus 002 Device 002: ID 046d:0840 Logitech, Inc. QuickCam Express

Later I installed from repositorio gspca-source (sudo aptitude install gspca-source), then I did unpack and I saw:

tricky@tricky-desktop:/usr/src/modules/gspca

Conexant   decoder       gspca.h       Mars-Semi         Sunplus       Vimicro
cutlog.py  Etoms         license       Pixart            Sunplus-jpeg
changelog  gspca_build   Makefile      READ_AND_INSTALL  Transvision
debian     gspca_core.c  Makefile.kld  Sonix             utils

Then I did sudo make, but it finalized with error:

make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 2
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [default] Error 2

(headers of my nucleo 2.6.27-7 (from uname -a) y had installed before - I didnt have any problem with install it from repositorio)

Then I downloaded source code from sourge forge, I compiled it, then I loaded the modul in the kernel, but the camera doesnt work

There I put something of lsmod
Module                  Size  Used by

videodev               41344  1 quickcam
v4l1_compat            22404  1 videodev

usbcore               148848  5 quickcam,usbhid,ohci_hcd,ehci_hcd

In what consist the problem? I wait your advices. Thanks in advance!

P.S.:
I have a driver for windows that work with my camera, by the way, ¿doesnt exist something like a ndiswrapper but no for wifi, for cameras?
:p

---

