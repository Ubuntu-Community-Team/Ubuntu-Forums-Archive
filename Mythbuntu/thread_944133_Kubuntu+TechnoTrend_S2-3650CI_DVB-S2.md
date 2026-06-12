---
title: "Kubuntu+TechnoTrend S2-3650CI DVB-S2"
date: 2008-10-11
forum: Mythbuntu
---

### Post by Sathumax on 2008-10-11
Hi guy's
I have try to install this hardware with the help of this wiki:
[Technotrend 3650]("http://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-3650_CI")

But I get stock on:
insmod dvb-core.ko

when i put this I get an error no such file or directory.:confused:

So where to find the file?
Or what shall i do?

---

### Post by Sathumax on 2008-10-11
> **Sathumax said:**
> Hi guy's
I have try to install this hardware with the help of this wiki:
[Technotrend 3650]("http://www.linuxtv.org/wiki/index.php/TechnoTrend_TT-connect_S2-3650_CI")

But I get stock on:
insmod dvb-core.ko

when i put this I get an error no such file or directory.:confused:

So where to find the file?
Or what shall i do?

root@DirectHome:/home/krystian/pctv452e/multiproto# make
make -C /home/krystian/pctv452e/multiproto/v4l
make[1]: Wej&#347;cie do katalogu `/home/krystian/pctv452e/multiproto/v4l'
scripts/make_makefile.pl
./scripts/make_myconfig.pl
make[1]: Opuszczenie katalogu `/home/krystian/pctv452e/multiproto/v4l'
make[1]: Wej&#347;cie do katalogu `/home/krystian/pctv452e/multiproto/v4l'
perl scripts/make_config_compat.pl /lib/modules/2.6.26.5/source ./.myconfig ./config-compat.h
creating symbolic links...
ln -sf . oss
Kernel build directory is /lib/modules/2.6.26.5/build
make -C /lib/modules/2.6.26.5/build SUBDIRS=/home/krystian/pctv452e/multiproto/v4l  modules
make[2]: Entering directory `/usr/src/linux-2.6.26'
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-pci.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-usb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-fe-tuner.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-i2c.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-sram.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-eeprom.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-misc.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-hw-filter.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/flexcop-dma.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-driver.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-driver.c:46:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-driver.c:38:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-cards.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-cards.c:40:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/linux/delay.h:10,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-cards.c:28:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-if.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-if.c:34:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-if.c:29:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-if.c:34:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-if.c:29:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-risc.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-risc.c:35:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-risc.c:27:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-vbi.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-vbi.c:33:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-vbi.c:26:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-i2c.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-i2c.c:34:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-i2c.c:30:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-gpio.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-gpio.c:35:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-gpio.c:29:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-gpio.c:35:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-gpio.c:29:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-input.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-input.c:28:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-input.c:21:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/bttv-audio-hook.o
In file included from /home/krystian/pctv452e/multiproto/v4l/bttv-audio-hook.h:8,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-audio-hook.c:8:
/home/krystian/pctv452e/multiproto/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/asm/system.h:10,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/wait.h:22,
                 from /home/krystian/pctv452e/multiproto/v4l/bttvp.h:32,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-audio-hook.h:8,
                 from /home/krystian/pctv452e/multiproto/v4l/bttv-audio-hook.c:8:
include/linux/kernel.h:379:1: warning: this is the location of the previous definition
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cpia2_v4l.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cpia2_usb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cpia2_core.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx23885-cards.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx23885-video.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx23885-vbi.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx23885-core.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx23885-i2c.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx23885-dvb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx25840-core.o
In file included from /home/krystian/pctv452e/multiproto/v4l/cx25840-core.c:42:
/home/krystian/pctv452e/multiproto/v4l/../linux/include/media/v4l2-i2c-drv-legacy.h: In function 'v4l2_i2c_drv_init':
/home/krystian/pctv452e/multiproto/v4l/../linux/include/media/v4l2-i2c-drv-legacy.h:201: warning: assignment from incompatible pointer type
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx25840-audio.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx25840-firmware.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx25840-vbi.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-video.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-vbi.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-mpeg.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-cards.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-core.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-i2c.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-tvaudio.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cx88-input.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110_hw.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110_v4l.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110_av.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110_ca.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110_ipack.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/av7110_ir.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/a800.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/af9005-remote.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/af9005.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/af9005-fe.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/au6610.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/cxusb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dib0700_core.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dib0700_devices.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dibusb-common.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dibusb-mb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dibusb-mc.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/digitv.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dtt200u.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dtt200u-fe.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/gl861.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/gp8psk.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/gp8psk-fe.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/m920x.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/nova-t-usb2.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/opera1.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ttusb2.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/umt-010.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/vp702x.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/vp702x-fe.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/vp7045.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/vp7045-fe.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dvb-usb-firmware.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dvb-usb-init.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dvb-usb-urb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dvb-usb-i2c.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dvb-usb-dvb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/dvb-usb-remote.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/usb-urb.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/em28xx-audio.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/em28xx-video.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/em28xx-i2c.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/em28xx-cards.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/em28xx-core.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/em28xx-input.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/et61x251_core.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ir-functions.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ir-keymaps.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-routing.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-cards.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-controls.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-driver.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-fileops.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-firmware.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-gpio.o
  CC [M]  /home/krystian/pctv452e/multiproto/v4l/ivtv-i2c.o
/home/krystian/pctv452e/multiproto/v4l/ivtv-i2c.c: In function 'ivtv_i2c_register':
/home/krystian/pctv452e/multiproto/v4l/ivtv-i2c.c:171: error: 'struct i2c_board_info' has no member named 'driver_name'
make[3]: *** [/home/krystian/pctv452e/multiproto/v4l/ivtv-i2c.o] Error 1
make[2]: *** [_module_/home/krystian/pctv452e/multiproto/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.26'
make[1]: *** [default] B&#322;&#261;d 2
make[1]: Opuszczenie katalogu `/home/krystian/pctv452e/multiproto/v4l'
make: *** [all] B&#322;&#261;d 2
root@DirectHome:/home/krystian/pctv452e/multiproto# cd v4l
root@DirectHome:/home/krystian/pctv452e/multiproto/v4l# ls *.ko
ls: nie ma dost&#281;pu do *.ko: No such file or directory
root@DirectHome:/home/krystian/pctv452e/multiproto/v4l# dir

In the directory v4l is no file like:
dvb-core.ko  dvb-usb-pctv452e.ko  dvb-usb.ko  lnbp22.ko  stb0899.ko  stb6100.ko
Why??
So it is not possible to do a:

insmod ./dvb-core.ko
insmod ./dvb-usb.ko
insmod ./lnbp22.ko
insmod ./stb0899.ko
insmod ./stb6100.ko
insmod ./dvb-usb-pctv452e.ko

---

### Post by Sathumax on 2008-10-11
Is this the right way guys?

krystian@DirectHome:~$ dmesg | grep -i dvb

[   37.533424] dvb-usb: found a 'Technotrend TT Connect S2-3650-CI' in warm stat                            e.
[   37.536393] dvb-usb: will pass the complete MPEG2 transport stream to the sof                            tware demuxer.
[   37.536513] DVB: registering new adapter (Technotrend TT Connect S2-3650-CI)
[   37.926488] DVB: Unable to find symbol stb0899_attach()
[   37.926491] dvb-usb: no frontend was attached by 'Technotrend TT Connect S2-3                            650-CI'
[   37.926733] input: IR-receiver inside an USB DVB receiver as /devices/pci0000                            :00/0000:00:1d.7/usb5/5-4/input/input7
[   37.991121] dvb-usb: schedule remote query interval to 500 msecs.
[   37.991128] dvb-usb: Technotrend TT Connect S2-3650-CI successfully initializ                            ed and connected.
[   38.175979] usbcore: registered new interface driver dvb-usb-tt-connect-s2-36                            00-01.fw

What i must do next?

---

