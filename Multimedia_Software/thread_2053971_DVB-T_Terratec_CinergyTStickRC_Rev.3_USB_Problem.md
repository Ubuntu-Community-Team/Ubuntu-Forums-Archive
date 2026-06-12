---
title: "DVB-T Terratec CinergyTStickRC Rev.3 USB Problem"
date: 2012-09-06
forum: Multimedia Software
---

### Post by prinzpogo on 2012-09-06
Cheers,

yesterday I installed my USB-DVB-T-Receiver on my Kubuntu 12.04 (Kernel 3.2.0-30-generic-pae) and it worked fine. Today it seems to doesn't work anymore. When I do grep -i dvb it says:

[   22.069325] dvb_usb: disagrees about version of symbol rc_register_device
[   22.069329] dvb_usb: Unknown symbol rc_register_device (err -22)
[   22.069343] dvb_usb: disagrees about version of symbol rc_free_device
[   22.069345] dvb_usb: Unknown symbol rc_free_device (err -22)
[   22.069354] dvb_usb: disagrees about version of symbol rc_allocate_device
[   22.069356] dvb_usb: Unknown symbol rc_allocate_device (err -22)
[   22.069371] dvb_usb: disagrees about version of symbol rc_unregister_device
[   22.069373] dvb_usb: Unknown symbol rc_unregister_device (err -22)
[   22.070143] dvb_usb: disagrees about version of symbol rc_register_device
[   22.070146] dvb_usb: Unknown symbol rc_register_device (err -22)
[   22.070159] dvb_usb: disagrees about version of symbol rc_free_device
[   22.070161] dvb_usb: Unknown symbol rc_free_device (err -22)
[   22.070170] dvb_usb: disagrees about version of symbol rc_allocate_device
[   22.070172] dvb_usb: Unknown symbol rc_allocate_device (err -22)
[   22.070184] dvb_usb: disagrees about version of symbol rc_unregister_device
[   22.070186] dvb_usb: Unknown symbol rc_unregister_device (err -22)

and

pbe@machine:~/v4l-dvb$ make
make -C /home/pbe/v4l-dvb/v4l 
make[1]: Betrete Verzeichnis '/home/pbe/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 3.2.0

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at [http://kernel.org](http://kernel.org).
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

WARNING: You're using an obsolete driver! You shouldn't be using it!
         If you want anything new, you can use:
                [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git).
         The tree is still here just to preserve the development history.
         You've been warned.
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Verlasse Verzeichnis '/home/pbe/v4l-dvb/v4l'
make[1]: Betrete Verzeichnis '/home/pbe/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/3.2.0-30-generic-pae/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/pbe/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/pbe/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/pbe/v4l-dvb/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/pbe/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/3.2.0-30-generic-pae/build
make -C /lib/modules/3.2.0-30-generic-pae/build SUBDIRS=/home/pbe/v4l-dvb/v4l CFLAGS="-I../linux/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
make[2]: Entering directory `/usr/src/linux-headers-3.2.0-30-generic-pae'
  CC [M]  /home/pbe/v4l-dvb/v4l/tuner-xc2028.o
/home/pbe/v4l-dvb/v4l/tuner-xc2028.c: In function 'xc2028_set_params':
/home/pbe/v4l-dvb/v4l/tuner-xc2028.c:1178:5: error: 'T_DIGITAL_TV' undeclared (first use in this function)
/home/pbe/v4l-dvb/v4l/tuner-xc2028.c:1178:5: note: each undeclared identifier is reported only once for each function it appears in
/home/pbe/v4l-dvb/v4l/tuner-xc2028.c:1179:1: warning: control reaches end of non-void function [-Wreturn-type]
make[3]: *** [/home/pbe/v4l-dvb/v4l/tuner-xc2028.o] Fehler 1
make[2]: *** [_module_/home/pbe/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.2.0-30-generic-pae'
make[1]: *** [default] Fehler 2
make[1]: Verlasse Verzeichnis '/home/pbe/v4l-dvb/v4l'
make: *** [all] Fehler 2


Any ideas?

regards

PP

---

