---
title: "How do I install the webcam Philips SPC 900NC?"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by Numero on 2006-06-15
Hi everyone,

I bought this USB webcam today and it wont work.

Tried to install it using EasyCam2, but it doesnt fint any camera...

Also tried to compile the latest snapshot of pwc from
[http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)
which should have spc900nc support.

I first installed headers for the linux kernel and changed the path in the Makefile for pwc but still get errors

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-23/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
/bin/sh: scripts/mod/modpost: File or catalogue does not exist
make[2]: *** [__modpost] Error 127
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23'
make: *** [all] Error 2


Has anyone managed to get this webcam to work on Ubuntu? Please let me know how you did it!

Best regards
Steve

---

### Post by TobbeR on 2006-07-27
Hi
This is a late answer but I managed to install the PWC driver yesterday. Had the same error during Make but it turned out to be a faulty installation of the linux-headers. I did a re-install from Synaptic and then everything went fine, I really don't think you should change anything in the Makefile. BTW, I installed the driver on an old laptop with PCLINUX and that worked ok to.

Best regards
T

---

### Post by alci on 2006-08-29
Hi,

I just bought the exact same webcam, but am unsuccessful until now :

- I installed pwc latest snapshot source as a deb package (taken from [http://www.saillard.org/linux/pwc/debian/](http://www.saillard.org/linux/pwc/debian/) )

- I installed module-assistant and get it to install latest pwcdriver (I think)

- but I can't use the webcam. No /dev/video0 device is present on my system.

So here is the state of my system :

$ lsusb
Bus 002 Device 002: ID 0471:0329 Philips

This corresponds to a Philips SPC 900NC.

$ dmesg
[17186847.292000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17186848.352000] usbcore: registered new driver snd-usb-audio
[17186871.336000] Linux video capture interface: v1.00
[17186871.356000] pwc Philips webcam module version 10.0.7-unofficial loaded.
[17186871.356000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[17186871.360000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[17186871.360000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[17186871.360000] pwc Trace options: 0x00a1
[17186871.360000] usbcore: registered new driver Philips webcam

and :

$ lsmod | grep pwc
pwc                    90932  0
videodev               10144  1 pwc
v4l2_common             6080  1 pwc
usbcore               139076  6 pwc,snd_usb_audio,snd_usb_lib,ehci_hcd,uhci_hcd

So I think the driver isloaded and it detects the webcam.

BUT ls /dev/video* gives nothing.
Camoram says "Could not connect to device (/dev/video1). Check connection".

What am I missing ?

Thanks,

Franck

---

### Post by alci on 2006-08-29
Ok, I reply to myself.

Latest pwc was not used, as another pwc.ko module was installed (by restricted-modules package ?).

Also module-assistant puts the new module in /lib/modules/_kernel-version_/kernel/drivers/usb/media/ , but the old driver is in a sub-directory of this directory (pwc/) and this is where modprobe looks for it...

So I replaced /lib/modules/_kernel-version_/kernel/drivers/usb/media/pwc/pwc.ko with /lib/modules/_kernel-version_/kernel/drivers/usb/media/pwc.ko,  and the cam now works !

:KS

---

