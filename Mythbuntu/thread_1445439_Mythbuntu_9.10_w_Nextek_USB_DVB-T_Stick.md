---
title: "Mythbuntu 9.10 w/ Nextek USB DVB-T Stick"
date: 2010-04-02
forum: Mythbuntu
---

### Post by Grakul on 2010-04-02
Hi, all

I've been having loads of problems getting my Nextek USB Stick (On Windows, this installs using an AF9015 driver) to work under Mythbuntu. I'm using Mythbuntu 9.10. I am very new to Linux, and not really familiar with building downloaded source code. I downloaded Mercurial and got the code using hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb), but when I run make, I get the following output:

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

Of course, if I can get by without messing around with kernel stuff, all the better! All I want to do is get my USB stick working in MythTV. I picked "USB DVB Tuner" in the MythTV Backend tool, and I'm then supposed to have to pick a device ID, but I can't as that drop down is empty. If I continue anyway, by the time I get to Scan channels, I get "cannot open device" or somesuch.

Thanks
Grakul

---

### Post by Grakul on 2010-04-03
Just a quick update. I followed the instructions [on this thread]("http://ubuntuforums.org/showthread.php?t=1305228") for getting rid of my build error (although I have no idea what FIREDTV is), and was able to successfully build the v4l-dvb drivers without any errors. After the make, sudo make install also ran through without errors.

But after a reboot, the stick is still not detected in Kaffeine, and I have no /dev/dvb/ folder (I've read I should have that folder if the device was loaded successfully).

Any idea what I'm missing?

---

### Post by Grakul on 2010-04-03
After the reboot, I went into Applications -> System -> Hardware Drivers, and it found "Firmware for DVB cards" (Previously it told me there were no proprietary drivers found). It told me the system was using another version of the driver, but I intalled that one anyway. After a reboot, still no /dev/dvb/ folder. :(

Anyone know what I'm missing?

Cheers
Grakul

---

### Post by Grakul on 2010-04-03
If I unplug the device and plug it back in (to a different port, just in case my port isn't working), I get the following in dmesg:

```
[ 1078.224551] usb 1-2: USB disconnect, address 3
[ 1082.208131] usb 1-1: new full speed USB device using ohci_hcd and address 4
[ 1082.425352] usb 1-1: configuration #1 chosen from 1 choice
[ 1083.641028] af9015: tuner NXP TDA18218 not supported yet
[ 1083.668450] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:02.0/usb1/1-1/1-1:1.1/input/input9
[ 1083.668678] generic-usb 0003:15A4:9016.0003: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:02.0-1/input1
downs@apollo:~$ 
```

Ubuntu obviously identifies my device, but how do I use it? (And what does "tuner NXP TDA18218 not supported yet" mean?)

I'm still learning all this Linux stuff. I've been a Windows developer in various languages for about 12 years, but Linux is a *completely* different animal to me! ;)

Cheers
Grakul

---

### Post by Grakul on 2010-04-04
New update, I followed the instructions in [this post]("http://ubuntuforums.org/showthread.php?p=9071798#post9071798"), by executing the following commands:

```
wget http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw
```

```
sudo cp dvb-usb-af9015.fw /lib/firmware/$(uname -r)
```

```
sudo cp dvb-usb-af9015.fw /lib/firmware/
```

(madmak couldn't remember which folder to copy it into, so I just copied it into both.) After a reboot, I still didn't have a /dev/dvb/ folder, and the MythTV backend still couldn't open my card. Then I realised I should probably rebuild and sudo make install the driver again (duh), which I did. The make went through without errors, and showed some things I don't remember it showing last time. I was getting really hopeful. sudo make install also went through without a hitch, but after a reboot... still nothing. :(

So I went to [madmak's blog]("http://ubuntu-stash.blogspot.com/2008/11/geniatech-t328b-dvb-t-usb-freeview.html"), added "dvb-usb-af9015" to the end of /etc/modules. For good measure, I also ran 

sudo modprobe dvb-usb-af9015

Which didn't give any output (I guess that's a good thing because up to now I've been seeing "Couldn't find module x" whenevere I ran it).

Reboot... still nothing. Unplug and plug in the stick, still nothing. Am no longer getting the "Tuner unsupported" message. Here's what I saw in dmesg after plugging the stick back in:

```
[  598.624004] usb 1-1: USB disconnect, address 2
[  602.732070] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  602.949343] usb 1-1: configuration #1 chosen from 1 choice
```

We're getting somewhere!! :)

However, I still have no /dev/dvb folder, and when I try to add a new capture card in the MythTV Backend Setup, (I pick "DVB DTV Capture Card (v3.x)") there is still nothing in the "DVB Device Number" dropdown.

Any help would be very much appreciated!! :)

Thanks
Grakul

---

### Post by Grakul on 2010-04-04
After the reboot, I tried a make and sudo make install yet again, and then rebooted. Still no /dev/dvb folder, and after unplugging and plugging in the stick, the following shows in dmesg:

```
[  170.988501] usb 1-1: USB disconnect, address 2
[  176.724089] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  176.942049] usb 1-2: configuration #1 chosen from 1 choice
[  178.139225] af9015: tuner NXP TDA18218 not supported yet
[  178.155748] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input8
[  178.155974] generic-usb 0003:15A4:9016.0002: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:02.0-2/input1
```

I don't think it's a "new" development that "tuner NXP TDA18218 not supported yet" - I think I just didn't wait long enough last time to see that message. And why is it detecting my stick as a keyboard?

Cheers
Grakul

---

### Post by Grakul on 2010-04-05
Just found [this post]("https://patchwork.kernel.org/patch/81836/") about the "tuner not supported" issue. I'm trying it now, but I'm not sure if I have to re-make and re-make install after downloading it. Will let you guys know! :)

---

### Post by Grakul on 2010-04-05
No luck. Even after the following:

```
sudo make rminstall
make
sudo make install
sudo reboot
```

But I've just realised that the post I referred to previously doesn't purport to fix the "af9015: tuner NXP TDA18218 not supported yet" error, but another error about tuner id:179 not supported yet. So that's not the error I was getting.

*sigh* Oh well.... :-/

---

### Post by Grakul on 2010-04-05
Instead of using the generic v4l drivers, I downloaded, built and installed the af9015 drivers from [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/). After rebooting, and unplugging and plugging in my DVB stick, I get the following in dmesg:

```
[  103.174231] usb 1-2: USB disconnect, address 2
[  110.136069] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  110.353167] usb 1-2: configuration #1 chosen from 1 choice
[  110.384534] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input8
[  110.384717] generic-usb 0003:15A4:9016.0002: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:02.0-2/input1
[  118.148066] Clocksource tsc unstable (delta = -167366863 ns)
```

Nothing about a tuner not supported, but still no /dev/dvb/ directory. Also from what I've seen in my googling, I should be seeing something about "downloading firmware" from a particular directory, should I not? :(

---

### Post by madmak on 2010-04-06
Hia grakel im not actually on my linux box just now but iv been tring to shake my brains to remember how i got my usb stick to work on mythubuntu because it was a while ago that i solved this but if you open a terminal and type

```
sudo find / adapter0 |grep adapter0
```

im positive the adapter0, dvb0, frontend0 and im sure theres 1 more file that ends in an 0 that should be in the /dev/dvb folder where in a different folder (maybe just the /dev folder) so if the search turns up a result for adapter0 then you just have to create the /dev/dvb folder and create symlinks in the /dev/dvb folder pointing to where the adapter0, dvb0, frontend0 and the other file is on your system.

Hope that helps if not ill have a look and see if i still have mythubuntu on a disk and install it tomorrow to see if i can figure it out again.

Btw i remember that for some reason when you have mythtv installed kaffeine wont be able to see your card unless you kill the mythtv backend with "sudo killall mythbackend"

---

### Post by Grakul on 2010-04-07
> **madmak said:**
> Hia grakel im not actually on my linux box just now but iv been tring to shake my brains to remember how i got my usb stick to work on mythubuntu because it was a while ago that i solved this but if you open a terminal and type

```
sudo find / adapter0 |grep adapter0
```

im positive the adapter0, dvb0, frontend0 and im sure theres 1 more file that ends in an 0 that should be in the /dev/dvb folder where in a different folder (maybe just the /dev folder) so if the search turns up a result for adapter0 then you just have to create the /dev/dvb folder and create symlinks in the /dev/dvb folder pointing to where the adapter0, dvb0, frontend0 and the other file is on your system.

Thanks so much! I'll have a look tonight! :)

> **madmak said:**
> Hope that helps if not ill have a look and see if i still have mythubuntu on a disk and install it tomorrow to see if i can figure it out again.

I would not expect you to do that, but am absolutely amazed that you would be willing to. Thanks!!

> **madmak said:**
> Btw i remember that for some reason when you have mythtv installed kaffeine wont be able to see your card unless you kill the mythtv backend with "sudo killall mythbackend"

Yes, I read that in your blog post. It makes sense. I actually uninstalled Kaffeine, and am using the following command to test the stick:

```
scan /usr/share/dvb/dvb-t/uk-WinterHill | tee channels.conf
```

(I'm not actually in WinterHill in the UK--I'm in South Africa; I just want the scan to actually *do* something, even if it fails with no results) ;)

I got that command from [http://parker1.co.uk/mythtv_dvb.php]("http://parker1.co.uk/mythtv_dvb.php"), and that tutorial also tells you to stop the mythtv-backend service first.

Thanks again!

Grakul

---

### Post by Grakul on 2010-04-07
Sorry, madmak

I rebuilt the v4l-dvb drivers, installed them, rebooted, disconnected and reconnected the stick, and did the following:

```
$ sudo find / adapter0 |grep adapter0
```

To which the result was:

```
find: `adapter0': No such file or directory
```

:(

Thanks anyway!
Grakul

---

### Post by Grakul on 2010-04-09
OK, so I re-installed Mythbuntu 9.10 from scratch, and then downloaded the firmware as suggested by madmak in [this thread]("http://ubuntuforums.org/showthread.php?t=1305228"). I now get the following in dmesg when I unplug and plug in the card:

```
[  141.520072] usb 1-2: new full speed USB device using ohci_hcd and address 3
[  141.736720] usb 1-2: configuration #1 chosen from 1 choice
[  141.795496] af9015: tuner id:179 not supported, please report!
[  141.816417] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.1/input/input8
[  141.816653] generic-usb 0003:15A4:9016.0002: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:02.0-2/input1
```

In Applications -> System -> Hardware Drivers, Mythbuntu suggested a "Firmware for DVB Cards"--I activated that and rebooted. Still nothing. :(

Cheers
Grakul

---

### Post by Grakul on 2010-04-09
OK, so I started [this thread]("http://ubuntuforums.org/showthread.php?p=9098437#post9098437") over at the hardware forum. Maybe they'll be able to help me.

---

### Post by Grakul on 2010-04-13
/me does a little dance

I got it working! I got it working!

I followed the instructions by tomerzz on the AF9015 thread:

> **tomerzz said:**
> try the following (all info gathered from this thread...)

hg clone -r 0f41fd7df85d [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/)

Firmware:
> wget http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link>
 sudo mv dvb-usb-af9015.fw_a-link /lib/firmware/dvb-usb-af9015.fw

cd af9015

copy the patch file from here
[http://www.mail-archive.com/linux-media@vger.kernel.org/msg16117.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg16117.html)
and save it to patch.txt

patch -p1 <patch.txt 

disable the firedtv driver by modifying the./v4l/.config file and changing '=m' to '=n' on the firedtv line.
and then..
make
sudo make install

My DVB Stick is detected in mythtv-backend, and I now have a /dev/dvb/ folder!

I can't get it to lock onto any channels currently, but that's a topic for another thread (which I'll start if I don't come right).

When I get some time, I'll perhaps write a blog entry about this.

Thanks to everyone to tried to help!

Cheers
Grakul

---

