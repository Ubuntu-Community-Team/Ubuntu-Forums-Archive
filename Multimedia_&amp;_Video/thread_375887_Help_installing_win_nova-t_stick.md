---
title: "Help installing win nova-t stick"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by Heedbanger on 2007-03-04
Hi I am trying to get my win nova t-stick working but am having problems.

I am following this guide: [http://www.ubuntuforums.org/newthread.php?do=newthread&f=138](http://www.ubuntuforums.org/newthread.php?do=newthread&f=138)

I have done the part with lsmod and found the the drivers for my nova-t missing but added them using modprobe so now when i do lsmod they are there.

The next part of the guide says i should now have stuff in: /dev/dvb/adaptor0/
I do not have this folder, but read on the linux tv site that ubontu stores them elsewhere.
 I downloaded the firmware for my nova-t and placed it in the firmware folder where the ones ubuntu already installed are.

I continued on with the rest of the guide to download and install V4l but i get errors when I try to run make.  

I would really appreciate any help to get this working as getting tv is about the only thing left that i stil need to use windows xp for.


Below is what happens when I try to run make:
dave@heedbanger:~/v4l-dvb$ sudo make
make -C /home/dave/v4l-dvb/v4l 
make[1]: Entering directory `/home/dave/v4l-dvb/v4l'
scripts/make_makefile.pl
No version yet.
Updating/Creating .config
Preparing to compile for kernel version 2.6.17

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

VIDEO_PLANB: Requires at least kernel 2.6.99
VIDEO_CAFE_CCIC: Requires at least kernel 2.6.19
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/dave/v4l-dvb/v4l'
make[1]: Entering directory `/home/dave/v4l-dvb/v4l'
creating symbolic links...
ln -sf . oss
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/dave/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-i2c.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-sram.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-eeprom.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-misc.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-hw-filter.o
  CC [M]  /home/dave/v4l-dvb/v4l/flexcop-dma.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-driver.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-cards.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-if.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-risc.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-vbi.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-i2c.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-gpio.o
  CC [M]  /home/dave/v4l-dvb/v4l/bttv-input.o
  CC [M]  /home/dave/v4l-dvb/v4l/cpia2_v4l.o
  CC [M]  /home/dave/v4l-dvb/v4l/cpia2_usb.o
  CC [M]  /home/dave/v4l-dvb/v4l/cpia2_core.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx25840-core.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx25840-audio.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx25840-firmware.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx25840-vbi.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-video.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-vbi.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-mpeg.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-cards.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-core.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-i2c.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-tvaudio.o
  CC [M]  /home/dave/v4l-dvb/v4l/cx88-input.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvbdev.o
  CC [M]  /home/dave/v4l-dvb/v4l/dmxdev.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_net.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb_math.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110_hw.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110_v4l.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110_av.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110_ca.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110_ipack.o
  CC [M]  /home/dave/v4l-dvb/v4l/av7110_ir.o
  CC [M]  /home/dave/v4l-dvb/v4l/a800.o
  CC [M]  /home/dave/v4l-dvb/v4l/au6610.o
  CC [M]  /home/dave/v4l-dvb/v4l/cxusb.o
  CC [M]  /home/dave/v4l-dvb/v4l/dib0700_core.o
  CC [M]  /home/dave/v4l-dvb/v4l/dib0700_devices.o
  CC [M]  /home/dave/v4l-dvb/v4l/dibusb-common.o
  CC [M]  /home/dave/v4l-dvb/v4l/dibusb-mb.o
  CC [M]  /home/dave/v4l-dvb/v4l/dibusb-mc.o
  CC [M]  /home/dave/v4l-dvb/v4l/digitv.o
  CC [M]  /home/dave/v4l-dvb/v4l/dtt200u.o
  CC [M]  /home/dave/v4l-dvb/v4l/dtt200u-fe.o
  CC [M]  /home/dave/v4l-dvb/v4l/gl861.o
  CC [M]  /home/dave/v4l-dvb/v4l/gp8psk.o
  CC [M]  /home/dave/v4l-dvb/v4l/gp8psk-fe.o
  CC [M]  /home/dave/v4l-dvb/v4l/m920x.o
  CC [M]  /home/dave/v4l-dvb/v4l/nova-t-usb2.o
  CC [M]  /home/dave/v4l-dvb/v4l/ttusb2.o
  CC [M]  /home/dave/v4l-dvb/v4l/umt-010.o
  CC [M]  /home/dave/v4l-dvb/v4l/vp702x.o
  CC [M]  /home/dave/v4l-dvb/v4l/vp702x-fe.o
  CC [M]  /home/dave/v4l-dvb/v4l/vp7045.o
  CC [M]  /home/dave/v4l-dvb/v4l/vp7045-fe.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb-usb-firmware.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb-usb-init.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb-usb-urb.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb-usb-i2c.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb-usb-dvb.o
  CC [M]  /home/dave/v4l-dvb/v4l/dvb-usb-remote.o
  CC [M]  /home/dave/v4l-dvb/v4l/usb-urb.o
  CC [M]  /home/dave/v4l-dvb/v4l/em28xx-video.o
  CC [M]  /home/dave/v4l-dvb/v4l/em28xx-i2c.o
  CC [M]  /home/dave/v4l-dvb/v4l/em28xx-cards.o
  CC [M]  /home/dave/v4l-dvb/v4l/em28xx-core.o
  CC [M]  /home/dave/v4l-dvb/v4l/em28xx-input.o
  CC [M]  /home/dave/v4l-dvb/v4l/et61x251_core.o
  CC [M]  /home/dave/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/dave/v4l-dvb/v4l/ir-functions.o
  CC [M]  /home/dave/v4l-dvb/v4l/ir-keymaps.o
  CC [M]  /home/dave/v4l-dvb/v4l/ivtv-audio.o
  CC [M]  /home/dave/v4l-dvb/v4l/ivtv-cards.o
  CC [M]  /home/dave/v4l-dvb/v4l/ivtv-controls.o
  CC [M]  /home/dave/v4l-dvb/v4l/ivtv-driver.o
/home/dave/v4l-dvb/v4l/ivtv-driver.c: In function 'ivtv_probe':
/home/dave/v4l-dvb/v4l/ivtv-driver.c:1170: error: 'IRQF_SHARED' undeclared (first use in this function)
/home/dave/v4l-dvb/v4l/ivtv-driver.c:1170: error: (Each undeclared identifier is reported only once
/home/dave/v4l-dvb/v4l/ivtv-driver.c:1170: error: for each function it appears in.)
/home/dave/v4l-dvb/v4l/ivtv-driver.c:1170: error: 'IRQF_DISABLED' undeclared (first use in this function)
make[3]: *** [/home/dave/v4l-dvb/v4l/ivtv-driver.o] Error 1
make[2]: *** [_module_/home/dave/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dave/v4l-dvb/v4l'
make: *** [all] Error 2

---

### Post by Titus A Duxass on 2008-03-02
Sorry, but your link at the top does not work correctly.

---

