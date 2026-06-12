---
title: "mythbuntu af9015 help please"
date: 2008-11-13
forum: Mythbuntu
---

### Post by madmak on 2008-11-13
Hia guys i was wondering if anyone has managed to get the af9015 chipset to work with Mythbuntu 8.10.

Iv not used mythbuntu before i downloaded it and installed it yesterday but im trying to get my Geniatech T328B usb dvb-t stick i got during the week to work on it, iv managed to get it working no problem on my standard ubuntu but have had no joy on mythbuntu the problem im having is that i dont seem to have the dvb stuff thats in /dev/dvb/adapter0/ on my normal ubuntu and the tutorials i used to make it work on ubuntu dont work for mythbuntu.

My drivers seem to be installed fine when i check in my hardware drivers app its just the /dev/dvb/adapter0/ part thats got me puzzled :confused:

Can anyone tell me how to fix this, if theres a work around for it in mythbuntu or point me to any links with a tutorial please.

---

### Post by madmak on 2008-11-13
hmmm it seems to be working now after i did

> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
sudo make install

i dont know if it was that thats fixed it or me unpluging it and pluging it in again but at least its working now :) :)

---

### Post by piginabox on 2009-03-07
AF9015 now works out-of-the-box with 9.04 Alpha 5.

cheers

---

### Post by Grakul on 2010-04-02
Hi, all

I'm really sorry for ressurecting this long-dead thread, but I've been having loads of problems getting my Nextek USB Stick (Using an AF9015 driver) to work under Mythbuntu. I'm using Mythbuntu 9.10. I am very new to Linux, and not really familiar with building downloaded source code. I downloaded Mercurial and got the code using hg clone, but when I run make, I get the following output:

```

downs@apollo:~/v4l-dvb$ make
make -C /home/downs/v4l-dvb/v4l 
make[1]: Entering directory `/home/downs/v4l-dvb/v4l'
No version yet, using 2.6.31-20-generic
make[1]: Leaving directory `/home/downs/v4l-dvb/v4l'
make[1]: Entering directory `/home/downs/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.31

***WARNING:*** You do not have the full kernel sources installed.
This does not prevent you from building the v4l-dvb tree if you have the
kernel headers, but the full kernel source may be required in order to use
make menuconfig / xconfig / qconfig.

If you are experiencing problems building the v4l-dvb tree, please try
building against a vanilla kernel before reporting a bug.

Vanilla kernels are available at http://kernel.org.
On most distros, this will compile a newly downloaded kernel:

cp /boot/config-`uname -r` <your kernel dir>/.config
cd <your kernel dir>
make all modules_install install

Please see your distro's web site for instructions to build a new kernel.

VIDEO_TVP7002: Requires at least kernel 2.6.34
SOC_CAMERA: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M001: Requires at least kernel 2.6.33
SOC_CAMERA_MT9M111: Requires at least kernel 2.6.33
SOC_CAMERA_MT9T031: Requires at least kernel 2.6.33
SOC_CAMERA_MT9V022: Requires at least kernel 2.6.33
SOC_CAMERA_TW9910: Requires at least kernel 2.6.33
SOC_CAMERA_PLATFORM: Requires at least kernel 2.6.33
SOC_CAMERA_OV772X: Requires at least kernel 2.6.33
VIDEO_PXA27x: Requires at least kernel 2.6.32
VIDEO_SH_MOBILE_CEU: Requires at least kernel 2.6.32
VIDEO_TLG2300: Requires at least kernel 2.6.32
RADIO_SAA7706H: Requires at least kernel 2.6.34
Created default (all yes) .config file
./scripts/make_myconfig.pl
make[1]: Leaving directory `/home/downs/v4l-dvb/v4l'
make[1]: Entering directory `/home/downs/v4l-dvb/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.31-20-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
make -C firmware prep
make[2]: Entering directory `/home/downs/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/downs/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/downs/v4l-dvb/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating dabusb/firmware.fw
Generating dabusb/bitstream.bin
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory `/home/downs/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-20-generic/build
make -C /lib/modules/2.6.31-20-generic/build SUBDIRS=/home/downs/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  CC [M]  /home/downs/v4l-dvb/v4l/tuner-xc2028.o
  CC [M]  /home/downs/v4l-dvb/v4l/tuner-simple.o
  CC [M]  /home/downs/v4l-dvb/v4l/tuner-types.o
  CC [M]  /home/downs/v4l-dvb/v4l/mt20xx.o
  CC [M]  /home/downs/v4l-dvb/v4l/tda8290.o
  CC [M]  /home/downs/v4l-dvb/v4l/tea5767.o
  CC [M]  /home/downs/v4l-dvb/v4l/tea5761.o
  CC [M]  /home/downs/v4l-dvb/v4l/tda9887.o
  CC [M]  /home/downs/v4l-dvb/v4l/tda827x.o
  CC [M]  /home/downs/v4l-dvb/v4l/au0828-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/au0828-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/au0828-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/au0828-dvb.o
  CC [M]  /home/downs/v4l-dvb/v4l/au0828-video.o
  CC [M]  /home/downs/v4l-dvb/v4l/au8522_dig.o
  CC [M]  /home/downs/v4l-dvb/v4l/au8522_decoder.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-pci.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-usb.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-fe-tuner.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-sram.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-eeprom.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-misc.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-hw-filter.o
  CC [M]  /home/downs/v4l-dvb/v4l/flexcop-dma.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-driver.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-if.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-risc.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-gpio.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-input.o
  CC [M]  /home/downs/v4l-dvb/v4l/bttv-audio-hook.o
  CC [M]  /home/downs/v4l-dvb/v4l/cpia2_v4l.o
  CC [M]  /home/downs/v4l-dvb/v4l/cpia2_usb.o
  CC [M]  /home/downs/v4l-dvb/v4l/cpia2_core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-alsa-main.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-alsa-pcm.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-driver.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-firmware.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-gpio.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-queue.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-streams.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-fileops.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-ioctl.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-controls.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-mailbox.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-audio.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-video.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-irq.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-av-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-av-audio.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-av-firmware.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-av-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-scb.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-dvb.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx18-io.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-audio.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-video.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-avcore.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-pcb-cfg.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx231xx-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-video.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-dvb.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-417.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-ioctl.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-ir.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-input.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23888-ir.o
  CC [M]  /home/downs/v4l-dvb/v4l/netup-init.o
  CC [M]  /home/downs/v4l-dvb/v4l/cimax2.o
  CC [M]  /home/downs/v4l-dvb/v4l/netup-eeprom.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx23885-f300.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx25840-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx25840-audio.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx25840-firmware.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx25840-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-video.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-mpeg.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-tvaudio.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-dsp.o
  CC [M]  /home/downs/v4l-dvb/v4l/cx88-input.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvbdev.o
  CC [M]  /home/downs/v4l-dvb/v4l/dmxdev.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_demux.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_filter.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_ca_en50221.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_frontend.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_net.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_ringbuffer.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb_math.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110_hw.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110_v4l.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110_av.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110_ca.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110_ipack.o
  CC [M]  /home/downs/v4l-dvb/v4l/av7110_ir.o
  CC [M]  /home/downs/v4l-dvb/v4l/a800.o
  CC [M]  /home/downs/v4l-dvb/v4l/af9005-remote.o
  CC [M]  /home/downs/v4l-dvb/v4l/af9005.o
  CC [M]  /home/downs/v4l-dvb/v4l/af9005-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/af9015.o
  CC [M]  /home/downs/v4l-dvb/v4l/anysee.o
  CC [M]  /home/downs/v4l-dvb/v4l/au6610.o
  CC [M]  /home/downs/v4l-dvb/v4l/az6027.o
  CC [M]  /home/downs/v4l-dvb/v4l/ce6230.o
  CC [M]  /home/downs/v4l-dvb/v4l/cinergyT2-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/cinergyT2-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/cxusb.o
  CC [M]  /home/downs/v4l-dvb/v4l/dib0700_core.o
  CC [M]  /home/downs/v4l-dvb/v4l/dib0700_devices.o
  CC [M]  /home/downs/v4l-dvb/v4l/dibusb-common.o
  CC [M]  /home/downs/v4l-dvb/v4l/dibusb-mb.o
  CC [M]  /home/downs/v4l-dvb/v4l/dibusb-mc.o
  CC [M]  /home/downs/v4l-dvb/v4l/digitv.o
  CC [M]  /home/downs/v4l-dvb/v4l/dtt200u.o
  CC [M]  /home/downs/v4l-dvb/v4l/dtt200u-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/dtv5100.o
  CC [M]  /home/downs/v4l-dvb/v4l/dw2102.o
  CC [M]  /home/downs/v4l-dvb/v4l/ec168.o
  CC [M]  /home/downs/v4l-dvb/v4l/friio.o
  CC [M]  /home/downs/v4l-dvb/v4l/friio-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/gl861.o
  CC [M]  /home/downs/v4l-dvb/v4l/gp8psk.o
  CC [M]  /home/downs/v4l-dvb/v4l/gp8psk-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/m920x.o
  CC [M]  /home/downs/v4l-dvb/v4l/nova-t-usb2.o
  CC [M]  /home/downs/v4l-dvb/v4l/opera1.o
  CC [M]  /home/downs/v4l-dvb/v4l/ttusb2.o
  CC [M]  /home/downs/v4l-dvb/v4l/umt-010.o
  CC [M]  /home/downs/v4l-dvb/v4l/vp702x.o
  CC [M]  /home/downs/v4l-dvb/v4l/vp702x-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/vp7045.o
  CC [M]  /home/downs/v4l-dvb/v4l/vp7045-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb-usb-firmware.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb-usb-init.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb-usb-urb.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb-usb-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb-usb-dvb.o
  CC [M]  /home/downs/v4l-dvb/v4l/dvb-usb-remote.o
  CC [M]  /home/downs/v4l-dvb/v4l/usb-urb.o
  CC [M]  /home/downs/v4l-dvb/v4l/pt1.o
  CC [M]  /home/downs/v4l-dvb/v4l/va1j5jf8007s.o
  CC [M]  /home/downs/v4l-dvb/v4l/va1j5jf8007t.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-audio.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-video.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-i2c.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-cards.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-core.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-input.o
  CC [M]  /home/downs/v4l-dvb/v4l/em28xx-vbi.o
  CC [M]  /home/downs/v4l-dvb/v4l/et61x251_core.o
/home/downs/v4l-dvb/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/downs/v4l-dvb/v4l/et61x251_core.c:2500: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/downs/v4l-dvb/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/downs/v4l-dvb/v4l/firedtv-avc.o
  CC [M]  /home/downs/v4l-dvb/v4l/firedtv-ci.o
  CC [M]  /home/downs/v4l-dvb/v4l/firedtv-dvb.o
  CC [M]  /home/downs/v4l-dvb/v4l/firedtv-fe.o
  CC [M]  /home/downs/v4l-dvb/v4l/firedtv-1394.o
/home/downs/v4l-dvb/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/downs/v4l-dvb/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/downs/v4l-dvb/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/downs/v4l-dvb/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:95: error: 'quadlet_t' undeclared (first use in this function)
/home/downs/v4l-dvb/v4l/firedtv-1394.c:95: error: (Each undeclared identifier is reported only once
/home/downs/v4l-dvb/v4l/firedtv-1394.c:95: error: for each function it appears in.)
/home/downs/v4l-dvb/v4l/firedtv-1394.c:95: error: 'd' undeclared (first use in this function)
/home/downs/v4l-dvb/v4l/firedtv-1394.c:96: warning: ISO C90 forbids mixed declarations and code
/home/downs/v4l-dvb/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_lock'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:99: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:107: error: implicit declaration of function 'hpsb_node_read'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:112: error: implicit declaration of function 'hpsb_node_write'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:123: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:123: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:125: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/downs/v4l-dvb/v4l/firedtv-1394.c:127: warning: assignment makes pointer from integer without a cast
/home/downs/v4l-dvb/v4l/firedtv-1394.c:134: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:137: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:148: error: implicit declaration of function 'hpsb_iso_stop'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/downs/v4l-dvb/v4l/firedtv-1394.c:163: warning: 'struct hpsb_host' declared inside parameter list
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:191: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:191: warning: type defaults to 'int' in declaration of '__mptr'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:191: warning: initialization from incompatible pointer type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:191: error: invalid use of undefined type 'struct unit_directory'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:198: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:198: warning: assignment makes pointer from integer without a cast
/home/downs/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/downs/v4l-dvb/v4l/firedtv-1394.c:257: warning: 'struct unit_directory' declared inside parameter list
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:259: error: dereferencing pointer to incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/downs/v4l-dvb/v4l/firedtv-1394.c:267: error: variable 'fdtv_driver' has initializer but incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:268: error: unknown field 'name' specified in initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:268: warning: excess elements in struct initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:268: warning: (near initialization for 'fdtv_driver')
/home/downs/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'id_table' specified in initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/downs/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'update' specified in initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/downs/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'driver' specified in initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:271: error: extra brace group at end of initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:271: error: (near initialization for 'fdtv_driver')
/home/downs/v4l-dvb/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_driver')
/home/downs/v4l-dvb/v4l/firedtv-1394.c:277: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/downs/v4l-dvb/v4l/firedtv-1394.c:278: error: unknown field 'name' specified in initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:278: warning: excess elements in struct initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:278: warning: (near initialization for 'fdtv_highlevel')
/home/downs/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'fcp_request' specified in initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/downs/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:286: error: implicit declaration of function 'hpsb_register_highlevel'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_protocol'
/home/downs/v4l-dvb/v4l/firedtv-1394.c:290: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/downs/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/downs/v4l-dvb/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/downs/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/downs/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/downs/v4l-dvb/v4l'
make: *** [all] Error 2
downs@apollo:~/v4l-dvb$ 

```

Can anyone tell me how I go about getting the full kernel source, or building against a vanilla kernel?

Thanks
Grakul

---

### Post by Grakul on 2010-04-02
Of course, if I can get by without messing around with kernel stuff, all the better! All I want to do is get my USB stick working in MythTV. I picked "USB DVB Tuner" in the MythTV Backend tool, and I'm then supposed to have to pick a device ID, but I can't as that drop down is empty. If I continue anyway, by the time I get to Scan channels, I get "cannot open device" or somesuch.

---

### Post by madmak on 2010-04-03
It may only be the firmware that your needing for it so open the terminal and try

```
wget http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw
```

then

```
sudo cp dvb-usb-af9015.fw /lib/firmware/$(uname -r)
```

or

```
sudo cp dvb-usb-af9015.fw /lib/firmware/
```

i cant remember exactly what folder it is so try both.

If your still having problems iv got a more detailed explanation of how to get the af9015 working on my blog heres a link if you need it but adding the firmware should work for you i think.

[http://ubuntu-stash.blogspot.com/2008/11/geniatech-t328b-dvb-t-usb-freeview.html](http://ubuntu-stash.blogspot.com/2008/11/geniatech-t328b-dvb-t-usb-freeview.html)

---

### Post by Grakul on 2010-04-04
Hi, madmak

Thanks very much for your help. But I still can't get it to work. :(

Since I posted my question on this thread, I actually decided to start a new thread, [here]("http://ubuntuforums.org/showthread.php?p=9073493"), where I'm documenting my experiences. Would you mind going to have a look at that thread, as I've done some other things which (in my ignorance) may have actually broken the situation further.

Thanks
Grakul

---

