---
title: "L4M-Twin CT2 Cannot make the drivers for 3.16.0-30-generic"
date: 2015-02-05
forum: Multimedia Software
---

### Post by tzorge on 2015-02-05
After installing latest headers, I cannot make the drivers.

I use the following command which has worked so far since Nov for all the updates.
 ```
  
cd /usr/src && sudo hg clone http://linuxtv.org/hg/~endriss/media_build_experimental/
 && cd media_build_experimental && 
sudo make download && 
sudo make untar && 
sudo make && 
sudo make install && 
sudo modprobe ddbridge  
``` 

dmseg is:
```
  dd0a6fe2bc3055cd61e369f97982c88183b1f0a0 [media] 
dvb-usb-dvbsky: fix i2c adapter for sp2 device

v4l-dvb-saa716x: d7e98fc592305a600909003da2b7cc4338242511 
saa716x_ff: Do not return on command ready timeout


```

I really am way in over my head, as i am rather noob in my understanding of linux.

Below is the entire dump from the commands i use to make and load the driver.

```
 user@ubuntu:/usr/src$ cd /usr/src && sudo hg clone http://linuxtv.org/hg/~endriss/media_build_experimental/ && cd media_build_experimental && sudo make download && sudo make untar && sudo make && sudo make install && sudo modprobe ddbridge
destination directory: media_build_experimental
requesting all changes
adding changesets
adding manifests
adding file changes
added 435 changesets with 1023 changes to 346 files
updating to branch default
289 files updated, 0 files merged, 0 files removed, 0 files unresolved
make -C linux/ download
make[1]: Entering directory '/usr/src/media_build_experimental/linux'
wget http://www.linuxtv.org/downloads/drivers/linux-media-2014-11-08-dd0a6fe.tar.bz2.md5 -O linux-media.tar.bz2.md5.tmp
--2015-02-08 12:10:04--  http://www.linuxtv.org/downloads/drivers/linux-media-2014-11-08-dd0a6fe.tar.bz2.md5
Resolving www.linuxtv.org (www.linuxtv.org)... 130.149.80.248
Connecting to www.linuxtv.org (www.linuxtv.org)|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 101 [application/x-bzip2]
Saving to: ‘linux-media.tar.bz2.md5.tmp’


100%[======================================>] 101         --.-K/s   in 0s      


2015-02-08 12:10:05 (15.3 MB/s) - ‘linux-media.tar.bz2.md5.tmp’ saved [101/101]


cat: linux-media.tar.bz2.md5: No such file or directory
--2015-02-08 12:10:05--  http://www.linuxtv.org/downloads/drivers/linux-media-2014-11-08-dd0a6fe.tar.bz2
Resolving www.linuxtv.org (www.linuxtv.org)... 130.149.80.248
Connecting to www.linuxtv.org (www.linuxtv.org)|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5100419 (4.9M) [application/x-bzip2]
Saving to: ‘linux-media.tar.bz2’


100%[======================================>] 5,100,419   1.18MB/s   in 5.5s   


2015-02-08 12:10:10 (905 KB/s) - ‘linux-media.tar.bz2’ saved [5100419/5100419]


make[1]: Leaving directory '/usr/src/media_build_experimental/linux'
make -C linux/ untar
make[1]: Entering directory '/usr/src/media_build_experimental/linux'
tar xfj linux-media.tar.bz2
rm -f .patches_applied .linked_dir .git_log.md5
../experimental/add-drivers


# Add ngene & octopus
rm -Rf ../linux/drivers/media/pci/{ddbridge,ngene} ../linux/drivers/staging/media/cxd2099/cxd2099*
cp -r dddvb/ddbridge ../linux/drivers/media/pci/
cp    oe/ddbridge/*  ../linux/drivers/media/pci/ddbridge/
cp -r oe/ngene       ../linux/drivers/media/pci/
# frontends
cp dddvb/frontends/cxd2099*    ../linux/drivers/staging/media/cxd2099/
cp dddvb/frontends/tda18212dd* ../linux/drivers/media/dvb-frontends/
cp dddvb/frontends/stv0367dd*  ../linux/drivers/media/dvb-frontends/
cp oe/drxk/*                   ../linux/drivers/media/dvb-frontends/
cp dddvb/frontends/cxd2843*    ../linux/drivers/media/dvb-frontends/
cp dddvb/frontends/lnbh25*     ../linux/drivers/media/dvb-frontends/
cp dddvb/frontends/stv6111*    ../linux/drivers/media/dvb-frontends/
cp dddvb/frontends/stv0910*    ../linux/drivers/media/dvb-frontends/
cp dddvb/frontends/mxl5xx*     ../linux/drivers/media/dvb-frontends/
# dvb-core extensions
cp dddvb/include/linux/dvb/mod.h   ../linux/include/uapi/linux/dvb/
cp dddvb/include/linux/dvb/ns.h    ../linux/include/uapi/linux/dvb/
cp dddvb/dvb-core/dvb_ca_en50221.* ../linux/drivers/media/dvb-core/
cp dddvb/dvb-core/dvb_netstream.*  ../linux/drivers/media/dvb-core/


# Add TT DVB S2-6400
fetch_hg_repo "https://bitbucket.org/powARman/v4l-dvb-saa716x" "v4l-dvb-saa716x" ||
 fetch_hg_repo "http://powarman.dyndns.org/hg/v4l-dvb-saa716x" "v4l-dvb-saa716x" ||
 fetch_hg_repo "http://linuxtv.org/hg/~endriss/mirror-saa716x" "v4l-dvb-saa716x"
requesting all changes
adding changesets
adding manifests
adding file changes
added 15472 changesets with 37961 changes to 2939 files
updating to branch default
1792 files updated, 0 files merged, 0 files removed, 0 files unresolved
rm -Rf ../linux/drivers/media/pci/saa716x
cp -r v4l-dvb-saa716x/linux/drivers/media/common/saa716x  ../linux/drivers/media/pci/
patch -d.. -p0 < saa716x.pci-kconfig.diff
patching file linux/drivers/media/pci/Kconfig
Hunk #1 succeeded at 49 with fuzz 2 (offset 5 lines).
patch -d.. -p0 < saa716x.pci-makefile.diff
patching file linux/drivers/media/pci/Makefile
patch -d.. -p0 < saa716x.include-osd.diff
patching file linux/include/uapi/linux/dvb/osd.h


for i in patch.d/*diff ;
do
    echo
    echo "Applying '$i'"
    apply_patch $i
done


Applying 'patch.d/010_dd-frontends-kconfig.diff'
patching file linux/drivers/media/dvb-frontends/Kconfig


Applying 'patch.d/010_dd-frontends-makefile.diff'
patching file linux/drivers/media/dvb-frontends/Makefile


Applying 'patch.d/010_dvb_netstream-makefile.diff'
patching file linux/drivers/media/dvb-core/Makefile


Applying 'patch.d/020_ddbridge-drxk.diff'
patching file linux/drivers/media/pci/ddbridge/ddbridge-core.c


Applying 'patch.d/030_ddbridge_pci_enable_msi_range.diff'
patching file linux/drivers/media/pci/ddbridge/ddbridge.c


Applying 'patch.d/031_ddbridge_attach_mxl5xx.diff'
patching file linux/drivers/media/pci/ddbridge/ddbridge-core.c


Applying 'patch.d/100_dvbdev.c.diff'
patching file linux/drivers/media/dvb-core/dvbdev.c
Hunk #3 succeeded at 84 with fuzz 2 (offset -7 lines).
Hunk #4 succeeded at 411 (offset -7 lines).
Hunk #5 succeeded at 433 (offset -7 lines).


Applying 'patch.d/100_dvbdev.h.diff'
patching file linux/drivers/media/dvb-core/dvbdev.h


Applying 'patch.d/100_frontend.h.diff'
patching file linux/include/uapi/linux/dvb/frontend.h


Applying 'patch.d/110_dvb_frontend.c_setinput.diff'
patching file linux/drivers/media/dvb-core/dvb_frontend.c


Applying 'patch.d/110_dvb_frontend.h_setinput.diff'
patching file drivers/media/dvb-core/dvb_frontend.h


Applying 'patch.d/110_frontend_setinput.diff'
patching file linux/include/uapi/linux/dvb/frontend.h


Applying 'patch.d/210_drxk_lockstatus_fix.diff'
patching file linux/drivers/media/dvb-frontends/drxk_hard.c


Applying 'patch.d/250_cxd28xx-qpsk-fix.diff'
patching file linux/drivers/media/dvb-frontends/cxd2843.c


Applying 'patch.d/251_cxd28xx-fec_4_5-2G_modulation-fix.diff'
patching file linux/drivers/media/dvb-frontends/cxd2843.c


Applying 'patch.d/310_set_tspath.diff'
patching file drivers/media/dvb-frontends/stv090x.c


Applying 'patch.d/315_get_coldlock.diff'
patching file drivers/media/dvb-frontends/stv090x.c


Applying 'patch.d/320_stv090x_ucblocks_ber.diff'
patching file linux/drivers/media/dvb-frontends/stv090x.c


Applying 'patch.d/399_stv090x_print_cut.diff'
patching file drivers/media/dvb-frontends/stv090x.c


Applying 'patch.d/800_av7110_discard_h264.diff'
patching file linux/drivers/media/pci/ttpci/av7110_ipack.c


Applying 'patch.d/810_av7110_fix_wss_regression.diff'
patching file linux/drivers/media/common/saa7146/saa7146_fops.c


Applying 'patch.d/900_DVB_MAX_ADAPTERS_32.diff'
patching file linux/drivers/media/dvb-core/Kconfig


Applying 'patch.d/990_dvb_demux_do_not_block_interrupts.diff'
patching file linux/drivers/media/dvb-core/dvb_demux.c


Applying 'patch.d/999_dvb_frontend_ratelimit_broken.diff'
patching file linux/drivers/media/dvb-core/dvb_frontend.c
Hunk #1 succeeded at 2437 (offset 9 lines).


Applying 'patch.d/999_dvb_frontend_show_fe_idx.diff'
patching file linux/drivers/media/dvb-core/dvb_frontend.c
Hunk #1 succeeded at 2654 (offset 9 lines).


# Drivers added successfully ;-)
make[1]: Leaving directory '/usr/src/media_build_experimental/linux'
make -C /usr/src/media_build_experimental/v4l 
make[1]: Entering directory '/usr/src/media_build_experimental/v4l'
No version yet, using 3.16.0-30-generic
scripts/make_makefile.pl
Updating/Creating .config
make[2]: Entering directory '/usr/src/media_build_experimental/linux'
Applying patches for kernel 3.16.0-30-generic
patch -s -f -N -p1 -i ../backports/api_version.patch
patch -s -f -N -p1 -i ../backports/pr_fmt.patch
patch -s -f -N -p1 -i ../backports/debug.patch
patch -s -f -N -p1 -i ../backports/drx39xxj.patch
patch -s -f -N -p1 -i ../backports/v3.16_netdev.patch
patch -s -f -N -p1 -i ../backports/v3.16_wait_on_bit.patch
patch -s -f -N -p1 -i ../backports/v3.16_void_gpiochip_remove.patch
Patched drivers/media/dvb-core/dvbdev.c
Patched drivers/media/v4l2-core/v4l2-dev.c
Patched drivers/media/rc/rc-main.c
make[2]: Leaving directory '/usr/src/media_build_experimental/linux'
Preparing to compile for kernel version 3.16.0


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


WARNING: This is the V4L/DVB backport tree, with experimental drivers
     backported to run on legacy kernels from the development tree at:
        http://git.linuxtv.org/media-tree.git.
     It is generally safe to use it for testing a new driver or
     feature, but its usage on production environments is risky.
     Don't use it in production. You've been warned.
Created default (all yes) .config file
make[2]: Entering directory '/usr/src/media_build_experimental/linux'
Patches for 3.16.0-30-generic already applied.
make[2]: Leaving directory '/usr/src/media_build_experimental/linux'
./scripts/make_kconfig.pl /lib/modules/3.16.0-30-generic/build /lib/modules/3.16.0-30-generic/build
Preparing to compile for kernel version 3.16.0


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


WARNING: This is the V4L/DVB backport tree, with experimental drivers
     backported to run on legacy kernels from the development tree at:
        http://git.linuxtv.org/media-tree.git.
     It is generally safe to use it for testing a new driver or
     feature, but its usage on production environments is risky.
     Don't use it in production. You've been warned.
../experimental/update_kconfig.pl
./scripts/make_myconfig.pl
perl scripts/make_config_compat.pl /lib/modules/3.16.0-30-generic/build ./.myconfig ./config-compat.h
creating symbolic links...
make -C firmware prep
make[2]: Entering directory '/usr/src/media_build_experimental/v4l/firmware'
make[2]: Leaving directory '/usr/src/media_build_experimental/v4l/firmware'
make -C firmware
make[2]: Entering directory '/usr/src/media_build_experimental/v4l/firmware'
  CC  ihex2fw
Generating vicam/firmware.fw
Generating ttusb-budget/dspbootcode.bin
Generating cpia2/stv0672_vp4.bin
Generating av7110/bootcode.bin
make[2]: Leaving directory '/usr/src/media_build_experimental/v4l/firmware'
Kernel build directory is /lib/modules/3.16.0-30-generic/build
make -C ../linux apply_patches
make[2]: Entering directory '/usr/src/media_build_experimental/linux'
Patches for 3.16.0-30-generic already applied.
make[2]: Leaving directory '/usr/src/media_build_experimental/linux'
make -C /lib/modules/3.16.0-30-generic/build SUBDIRS=/usr/src/media_build_experimental/v4l  modules
make[2]: Entering directory '/usr/src/linux-headers-3.16.0-30-generic'
  CC [M]  /usr/src/media_build_experimental/v4l/altera-lpt.o
  CC [M]  /usr/src/media_build_experimental/v4l/altera-jtag.o
  CC [M]  /usr/src/media_build_experimental/v4l/altera-comp.o
  CC [M]  /usr/src/media_build_experimental/v4l/altera.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/au0828-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-dma.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-pci.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-usb.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-fe-tuner.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-sram.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-eeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-misc.o
  CC [M]  /usr/src/media_build_experimental/v4l/flexcop-hw-filter.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-if.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-risc.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/bttv-audio-hook.o
  CC [M]  /usr/src/media_build_experimental/v4l/cafe-driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/mcam-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cpia2_v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/cpia2_usb.o
  CC [M]  /usr/src/media_build_experimental/v4l/cpia2_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-alsa-main.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-alsa-pcm.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-firmware.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-queue.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-streams.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-fileops.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-ioctl.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-controls.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-mailbox.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-irq.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-av-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-av-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-av-firmware.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-av-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-scb.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx18-io.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-avcore.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-417.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-pcb-cfg.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-417.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-ioctl.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-ir.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-av.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23888-ir.o
  CC [M]  /usr/src/media_build_experimental/v4l/netup-init.o
  CC [M]  /usr/src/media_build_experimental/v4l/cimax2.o
  CC [M]  /usr/src/media_build_experimental/v4l/netup-eeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-f300.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx23885-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-medusa-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-video-upstream.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25840-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25840-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25840-firmware.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25840-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25840-ir.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-mpeg.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-tvaudio.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-dsp.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxd2820r_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxd2820r_c.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxd2820r_t.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxd2820r_t2.o
  CC [M]  /usr/src/media_build_experimental/v4l/drxj.o
  CC [M]  /usr/src/media_build_experimental/v4l/drxd_firm.o
  CC [M]  /usr/src/media_build_experimental/v4l/drxd_hard.o
  CC [M]  /usr/src/media_build_experimental/v4l/drxk_hard.o
  CC [M]  /usr/src/media_build_experimental/v4l/as102_drv.o
  CC [M]  /usr/src/media_build_experimental/v4l/as102_fw.o
  CC [M]  /usr/src/media_build_experimental/v4l/as10x_cmd.o
  CC [M]  /usr/src/media_build_experimental/v4l/as10x_cmd_stream.o
  CC [M]  /usr/src/media_build_experimental/v4l/as102_usb_drv.o
  CC [M]  /usr/src/media_build_experimental/v4l/as10x_cmd_cfg.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvbdev.o
  CC [M]  /usr/src/media_build_experimental/v4l/dmxdev.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_demux.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_filter.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_ca_en50221.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_frontend.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_net.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_ringbuffer.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_math.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_netstream.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110_hw.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110_v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110_av.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110_ca.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110_ipack.o
  CC [M]  /usr/src/media_build_experimental/v4l/av7110_ir.o
  CC [M]  /usr/src/media_build_experimental/v4l/a800.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9005-remote.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9005.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9005-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9015.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9035.o
  CC [M]  /usr/src/media_build_experimental/v4l/anysee.o
  CC [M]  /usr/src/media_build_experimental/v4l/au6610.o
  CC [M]  /usr/src/media_build_experimental/v4l/az6007.o
  CC [M]  /usr/src/media_build_experimental/v4l/az6027.o
  CC [M]  /usr/src/media_build_experimental/v4l/ce6230.o
  CC [M]  /usr/src/media_build_experimental/v4l/cinergyT2-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/cinergyT2-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxusb.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib0700_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib0700_devices.o
  CC [M]  /usr/src/media_build_experimental/v4l/dibusb-common.o
  CC [M]  /usr/src/media_build_experimental/v4l/dibusb-mb.o
  CC [M]  /usr/src/media_build_experimental/v4l/dibusb-mc.o
  CC [M]  /usr/src/media_build_experimental/v4l/digitv.o
  CC [M]  /usr/src/media_build_experimental/v4l/dtt200u.o
  CC [M]  /usr/src/media_build_experimental/v4l/dtt200u-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/dtv5100.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvbsky.o
  CC [M]  /usr/src/media_build_experimental/v4l/dw2102.o
  CC [M]  /usr/src/media_build_experimental/v4l/ec168.o
  CC [M]  /usr/src/media_build_experimental/v4l/friio.o
  CC [M]  /usr/src/media_build_experimental/v4l/friio-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/gl861.o
  CC [M]  /usr/src/media_build_experimental/v4l/gp8psk.o
  CC [M]  /usr/src/media_build_experimental/v4l/gp8psk-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/lmedm04.o
  CC [M]  /usr/src/media_build_experimental/v4l/m920x.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl111sf.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl111sf-phy.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl111sf-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl111sf-gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/nova-t-usb2.o
  CC [M]  /usr/src/media_build_experimental/v4l/opera1.o
  CC [M]  /usr/src/media_build_experimental/v4l/pctv452e.o
  CC [M]  /usr/src/media_build_experimental/v4l/rtl28xxu.o
  CC [M]  /usr/src/media_build_experimental/v4l/technisat-usb2.o
  CC [M]  /usr/src/media_build_experimental/v4l/ttusb2.o
  CC [M]  /usr/src/media_build_experimental/v4l/umt-010.o
  CC [M]  /usr/src/media_build_experimental/v4l/vp702x.o
  CC [M]  /usr/src/media_build_experimental/v4l/vp702x-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/vp7045.o
  CC [M]  /usr/src/media_build_experimental/v4l/vp7045-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-usb-firmware.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-usb-init.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-usb-urb.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-usb-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-usb-remote.o
  CC [M]  /usr/src/media_build_experimental/v4l/usb-urb.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_usb_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_usb_urb.o
  CC [M]  /usr/src/media_build_experimental/v4l/usb_urb.o
  CC [M]  /usr/src/media_build_experimental/v4l/pt1.o
  CC [M]  /usr/src/media_build_experimental/v4l/va1j5jf8007s.o
  CC [M]  /usr/src/media_build_experimental/v4l/va1j5jf8007t.o
  CC [M]  /usr/src/media_build_experimental/v4l/pt3.o
  CC [M]  /usr/src/media_build_experimental/v4l/pt3_i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/pt3_dma.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-camera.o
  CC [M]  /usr/src/media_build_experimental/v4l/firedtv-avc.o
  CC [M]  /usr/src/media_build_experimental/v4l/firedtv-ci.o
  CC [M]  /usr/src/media_build_experimental/v4l/firedtv-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/firedtv-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/firedtv-fw.o
  CC [M]  /usr/src/media_build_experimental/v4l/firedtv-rc.o
  CC [M]  /usr/src/media_build_experimental/v4l/fmdrv_common.o
  CC [M]  /usr/src/media_build_experimental/v4l/fmdrv_rx.o
  CC [M]  /usr/src/media_build_experimental/v4l/fmdrv_tx.o
  CC [M]  /usr/src/media_build_experimental/v4l/fmdrv_v4l2.o
  CC [M]  /usr/src/media_build_experimental/v4l/go7007-v4l2.o
  CC [M]  /usr/src/media_build_experimental/v4l/go7007-driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/go7007-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/go7007-fw.o
  CC [M]  /usr/src/media_build_experimental/v4l/snd-go7007.o
  CC [M]  /usr/src/media_build_experimental/v4l/benq.o
  CC [M]  /usr/src/media_build_experimental/v4l/conex.o
  CC [M]  /usr/src/media_build_experimental/v4l/cpia1.o
  CC [M]  /usr/src/media_build_experimental/v4l/dtcs033.o
  CC [M]  /usr/src/media_build_experimental/v4l/etoms.o
  CC [M]  /usr/src/media_build_experimental/v4l/finepix.o
  CC [M]  /usr/src/media_build_experimental/v4l/gl860.o
  CC [M]  /usr/src/media_build_experimental/v4l/gl860-mi1320.o
  CC [M]  /usr/src/media_build_experimental/v4l/gl860-ov2640.o
  CC [M]  /usr/src/media_build_experimental/v4l/gl860-ov9655.o
  CC [M]  /usr/src/media_build_experimental/v4l/gl860-mi2020.o
  CC [M]  /usr/src/media_build_experimental/v4l/jeilinj.o
  CC [M]  /usr/src/media_build_experimental/v4l/jl2005bcd.o
  CC [M]  /usr/src/media_build_experimental/v4l/kinect.o
  CC [M]  /usr/src/media_build_experimental/v4l/konica.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_ov9650.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_ov7660.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_mt9m111.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_po1030.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_s5k83a.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5602_s5k4aa.o
  CC [M]  /usr/src/media_build_experimental/v4l/gspca.o
  CC [M]  /usr/src/media_build_experimental/v4l/autogain_functions.o
  CC [M]  /usr/src/media_build_experimental/v4l/mars.o
  CC [M]  /usr/src/media_build_experimental/v4l/mr97310a.o
  CC [M]  /usr/src/media_build_experimental/v4l/nw80x.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov519.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov534.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov534_9.o
  CC [M]  /usr/src/media_build_experimental/v4l/pac207.o
  CC [M]  /usr/src/media_build_experimental/v4l/pac7302.o
  CC [M]  /usr/src/media_build_experimental/v4l/pac7311.o
  CC [M]  /usr/src/media_build_experimental/v4l/se401.o
  CC [M]  /usr/src/media_build_experimental/v4l/sn9c2028.o
  CC [M]  /usr/src/media_build_experimental/v4l/sn9c20x.o
  CC [M]  /usr/src/media_build_experimental/v4l/sonixb.o
  CC [M]  /usr/src/media_build_experimental/v4l/sonixj.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca1528.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca500.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca501.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca505.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca506.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca508.o
  CC [M]  /usr/src/media_build_experimental/v4l/spca561.o
  CC [M]  /usr/src/media_build_experimental/v4l/sq905.o
  CC [M]  /usr/src/media_build_experimental/v4l/sq905c.o
  CC [M]  /usr/src/media_build_experimental/v4l/sq930x.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk014.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk1135.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0680.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv06xx.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv06xx_vv6410.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv06xx_hdcs.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv06xx_pb0100.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv06xx_st6422.o
  CC [M]  /usr/src/media_build_experimental/v4l/sunplus.o
  CC [M]  /usr/src/media_build_experimental/v4l/t613.o
  CC [M]  /usr/src/media_build_experimental/v4l/topro.o
  CC [M]  /usr/src/media_build_experimental/v4l/tv8532.o
  CC [M]  /usr/src/media_build_experimental/v4l/vc032x.o
  CC [M]  /usr/src/media_build_experimental/v4l/vicam.o
  CC [M]  /usr/src/media_build_experimental/v4l/xirlink_cit.o
  CC [M]  /usr/src/media_build_experimental/v4l/zc3xx.o
  CC [M]  /usr/src/media_build_experimental/v4l/hdpvr-control.o
  CC [M]  /usr/src/media_build_experimental/v4l/hdpvr-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/hdpvr-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/hdpvr-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/hopper_cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/hopper_vp3028.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-raw.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-hw.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-nec.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-jvc.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-sony.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-sharp.o
  CC [M]  /usr/src/media_build_experimental/v4l/img-ir-sanyo.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-alsa-main.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-alsa-pcm.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-routing.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-controls.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-fileops.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-firmware.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-ioctl.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-irq.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-mailbox.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-queue.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-streams.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-udma.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtv-yuv.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5mols_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5mols_controls.o
  CC [M]  /usr/src/media_build_experimental/v4l/m5mols_capture.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_vp1033.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_vp1034.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_vp1041.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_vp2033.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_vp2040.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_vp3030.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_ioc.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_uart.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_dma.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_pci.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_evm.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_hif.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_ca.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_pcmcia.o
  CC [M]  /usr/src/media_build_experimental/v4l/mantis_input.o
  CC [M]  /usr/src/media_build_experimental/v4l/media-device.o
  CC [M]  /usr/src/media_build_experimental/v4l/media-devnode.o
  CC [M]  /usr/src/media_build_experimental/v4l/media-entity.o
  CC [M]  /usr/src/media_build_experimental/v4l/msp3400-driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/msp3400-kthreads.o
  CC [M]  /usr/src/media_build_experimental/v4l/ngene-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/ngene-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/ngene-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/ngene-av.o
  CC [M]  /usr/src/media_build_experimental/v4l/ngene-eeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/ngene-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/pd-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/pd-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/pd-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/pd-radio.o
  CC [M]  /usr/src/media_build_experimental/v4l/pd-main.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-i2c-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-encoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-video-v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-eeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-main.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-hdw.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-v4l2.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-ctrl.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-std.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-devattr.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-context.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-io.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-ioread.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-cx2584x-v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-wm8775.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-cs53l32a.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-sysfs.o
  CC [M]  /usr/src/media_build_experimental/v4l/pvrusb2-debugifc.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-if.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-misc.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-ctrl.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-uncompress.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-dec1.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-dec23.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-kiara.o
  CC [M]  /usr/src/media_build_experimental/v4l/pwc-timon.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-si470x-usb.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-si470x-common.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-main.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-ir-raw.o
  CC [M]  /usr/src/media_build_experimental/v4l/s2250-board.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5c73m3-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5c73m3-spi.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5c73m3-ctrls.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-ts.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-tvaudio.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7146_i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7146_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7146_fops.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7146_video.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7146_hlp.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7146_vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-fw.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-bus.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-cmd.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-api.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-buffer.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-encoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7164-vbi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_pci.o
/usr/src/media_build_experimental/v4l/saa716x_pci.c:20:20: warning: 'saa716x_msi_handler' defined but not used [-Wunused-function]
 static irqreturn_t saa716x_msi_handler(int irq, void *dev_id)
                    ^
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_cgu.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_msi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_dma.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_vip.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_aip.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_phi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_boot.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_fgpi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_adap.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_greg.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_rom.o
In file included from /usr/src/media_build_experimental/v4l/saa716x_rom.c:7:0:
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_eeprom_header':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:117:19: warning: format '%d' expects argument of type 'int', but argument 4 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_romhdr),
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:117:19: warning: format '%d' expects argument of type 'int', but argument 4 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_romhdr),
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:117:19: warning: format '%d' expects argument of type 'int', but argument 4 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_romhdr),
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:117:19: warning: format '%d' expects argument of type 'int', but argument 4 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_romhdr),
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:117:19: warning: format '%d' expects argument of type 'int', but argument 2 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_romhdr),
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_decoder_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:242:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:242:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:242:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:242:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:242:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_gpio_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:273:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_gpio_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:273:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_gpio_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:273:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_gpio_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:273:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_gpio_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:273:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_gpio_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_video_decoder_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:310:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_video_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:310:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_video_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:310:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_video_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:310:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_video_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:310:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_video_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_audio_decoder_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:391:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_audio_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:391:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_audio_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:391:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_audio_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:391:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_audio_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:391:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_audio_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_event_source_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:422:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_evsrc_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:422:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_evsrc_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:422:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_evsrc_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:422:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_evsrc_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:422:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_evsrc_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_crossbar_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:453:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_xbar_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:453:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_xbar_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:453:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_xbar_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:453:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_xbar_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:453:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_xbar_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_tuner_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:491:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_tuner_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:491:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_tuner_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:491:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_tuner_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:491:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_tuner_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:491:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_tuner_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_pll_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:521:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_pll_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:521:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_pll_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:521:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_pll_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:521:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_pll_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:521:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_pll_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_channel_decoder_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:551:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_channel_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:551:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_channel_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:551:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_channel_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:551:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_channel_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:551:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_channel_decoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_encoder_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:581:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_encoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:581:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_encoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:581:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_encoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:581:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_encoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:581:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_encoder_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_ir_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:611:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_ir_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:611:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_ir_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:611:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_ir_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:611:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_ir_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:611:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_ir_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_eeprom_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:642:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_eeprom_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:642:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_eeprom_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:642:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_eeprom_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:642:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_eeprom_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:642:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_eeprom_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_filter_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:673:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_filter_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:673:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_filter_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:673:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_filter_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:673:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_filter_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:673:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_filter_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_streamdev_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:704:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_streamdev_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:704:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_streamdev_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:704:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_streamdev_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:704:19: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_streamdev_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:704:19: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
    sizeof (struct saa716x_streamdev_hdr));
                   ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_device_info':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:794:18: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
   sizeof (struct saa716x_devinfo));
                  ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:39:72: note: in definition of macro 'dprintk'
    printk(KERN_ERR "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                        ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:794:18: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
   sizeof (struct saa716x_devinfo));
                  ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:41:75: note: in definition of macro 'dprintk'
    printk(KERN_NOTICE "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                           ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:794:18: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
   sizeof (struct saa716x_devinfo));
                  ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:43:73: note: in definition of macro 'dprintk'
    printk(KERN_INFO "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                         ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:794:18: warning: format '%d' expects argument of type 'int', but argument 5 has type 'long unsigned int' [-Wformat=]
   sizeof (struct saa716x_devinfo));
                  ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:45:74: note: in definition of macro 'dprintk'
    printk(KERN_DEBUG "%s (%d): " __fmt "\n" , __func__ , SAA716x_DEV , ##__arg); \
                                                                          ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c:794:18: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat=]
   sizeof (struct saa716x_devinfo));
                  ^
/usr/src/media_build_experimental/v4l/saa716x_priv.h:48:21: note: in definition of macro 'dprintk'
    printk(__fmt , ##__arg);       \
                     ^
/usr/src/media_build_experimental/v4l/saa716x_rom.c: In function 'saa716x_eeprom_data':
/usr/src/media_build_experimental/v4l/saa716x_rom.c:1070:1: warning: the frame size of 1136 bytes is larger than 1024 bytes [-Wframe-larger-than=]
 }
 ^
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_spi.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_ff_main.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_ff_cmd.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_ff_ir.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_ff_phi.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-shark2.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-tea5777.o
  CC [M]  /usr/src/media_build_experimental/v4l/smiapp-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/smiapp-regs.o
  CC [M]  /usr/src/media_build_experimental/v4l/smiapp-quirk.o
  CC [M]  /usr/src/media_build_experimental/v4l/smiapp-limits.o
  CC [M]  /usr/src/media_build_experimental/v4l/smsdvb-main.o
  CC [M]  /usr/src/media_build_experimental/v4l/smsdvb-debugfs.o
  CC [M]  /usr/src/media_build_experimental/v4l/smscoreapi.o
  CC [M]  /usr/src/media_build_experimental/v4l/sms-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/smsendian.o
  CC [M]  /usr/src/media_build_experimental/v4l/smsir.o
  CC [M]  /usr/src/media_build_experimental/v4l/bt87x.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-p2m.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-v4l2.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-tw28.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-gpio.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-disp.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-enc.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-v4l2-enc.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-g723.o
  CC [M]  /usr/src/media_build_experimental/v4l/solo6x10-eeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/stb0899_drv.o
  CC [M]  /usr/src/media_build_experimental/v4l/stb0899_algo.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk1160-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk1160-v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk1160-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk1160-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk1160-ac97.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk-webcam.o
  CC [M]  /usr/src/media_build_experimental/v4l/stk-sensor.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0900_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0900_sw.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18271-maps.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18271-common.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18271-fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-stds.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-input.o
  CC [M]  /usr/src/media_build_experimental/v4l/tuner-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw68-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw68-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw68-risc.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbtv-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbtv-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbtv-audio.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbvision-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbvision-video.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbvision-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/usbvision-cards.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_queue.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_v4l2.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_video.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_ctrl.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_status.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_isight.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_debugfs.o
  CC [M]  /usr/src/media_build_experimental/v4l/uvc_entity.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-dev.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-ioctl.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-device.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-fh.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-event.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-ctrls.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-subdev.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-clk.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-async.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-compat-ioctl32.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-ctrls.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-vid-common.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-vbi-gen.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-vid-cap.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-vid-out.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-kthread-cap.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-kthread-out.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-radio-rx.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-radio-tx.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-radio-common.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-rds-gen.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-sdr-cap.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-vbi-cap.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-vbi-out.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-osd.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-tpg.o
  CC [M]  /usr/src/media_build_experimental/v4l/vivid-tpg-colors.o
  CC [M]  /usr/src/media_build_experimental/v4l/zoran_procfs.o
  CC [M]  /usr/src/media_build_experimental/v4l/zoran_device.o
  CC [M]  /usr/src/media_build_experimental/v4l/zoran_driver.o
  CC [M]  /usr/src/media_build_experimental/v4l/zoran_card.o
  LD [M]  /usr/src/media_build_experimental/v4l/msp3400.o
  LD [M]  /usr/src/media_build_experimental/v4l/smiapp.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx25840.o
  LD [M]  /usr/src/media_build_experimental/v4l/m5mols.o
  CC [M]  /usr/src/media_build_experimental/v4l/imx074.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9m001.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9m111.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9t031.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9t112.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9v022.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov2640.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov5642.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov6650.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov772x.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov9640.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov9740.o
  CC [M]  /usr/src/media_build_experimental/v4l/rj54n1cb0c.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw9910.o
  CC [M]  /usr/src/media_build_experimental/v4l/aptina-pll.o
  CC [M]  /usr/src/media_build_experimental/v4l/tvaudio.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda7432.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa6588.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda9840.o
  CC [M]  /usr/src/media_build_experimental/v4l/tea6415c.o
  CC [M]  /usr/src/media_build_experimental/v4l/tea6420.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7110.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7115.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa717x.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7127.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7185.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7191.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa6752hs.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7170.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7175.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7180.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7183.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7343.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7393.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7604.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7842.o
  CC [M]  /usr/src/media_build_experimental/v4l/ad9389b.o
  CC [M]  /usr/src/media_build_experimental/v4l/adv7511.o
  CC [M]  /usr/src/media_build_experimental/v4l/vpx3220.o
  CC [M]  /usr/src/media_build_experimental/v4l/vs6624.o
  CC [M]  /usr/src/media_build_experimental/v4l/bt819.o
  CC [M]  /usr/src/media_build_experimental/v4l/bt856.o
  CC [M]  /usr/src/media_build_experimental/v4l/bt866.o
  CC [M]  /usr/src/media_build_experimental/v4l/ks0127.o
  CC [M]  /usr/src/media_build_experimental/v4l/ths7303.o
  CC [M]  /usr/src/media_build_experimental/v4l/ths8200.o
  CC [M]  /usr/src/media_build_experimental/v4l/tvp5150.o
  CC [M]  /usr/src/media_build_experimental/v4l/tvp514x.o
  CC [M]  /usr/src/media_build_experimental/v4l/tvp7002.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw2804.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw9903.o
  CC [M]  /usr/src/media_build_experimental/v4l/tw9906.o
  CC [M]  /usr/src/media_build_experimental/v4l/cs5345.o
  CC [M]  /usr/src/media_build_experimental/v4l/cs53l32a.o
  CC [M]  /usr/src/media_build_experimental/v4l/m52790.o
  CC [M]  /usr/src/media_build_experimental/v4l/tlv320aic23b.o
  CC [M]  /usr/src/media_build_experimental/v4l/uda1342.o
  CC [M]  /usr/src/media_build_experimental/v4l/wm8775.o
  CC [M]  /usr/src/media_build_experimental/v4l/wm8739.o
  CC [M]  /usr/src/media_build_experimental/v4l/vp27smpx.o
  CC [M]  /usr/src/media_build_experimental/v4l/sony-btf-mpx.o
  CC [M]  /usr/src/media_build_experimental/v4l/upd64031a.o
  CC [M]  /usr/src/media_build_experimental/v4l/upd64083.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov7640.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov7670.o
  CC [M]  /usr/src/media_build_experimental/v4l/ov9650.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9m032.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9p031.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9t001.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9v011.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt9v032.o
  CC [M]  /usr/src/media_build_experimental/v4l/sr030pc30.o
  CC [M]  /usr/src/media_build_experimental/v4l/noon010pc30.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5k6aa.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5k6a3.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5k4ecgx.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5k5baf.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5c73m3.o
  CC [M]  /usr/src/media_build_experimental/v4l/adp1653.o
  CC [M]  /usr/src/media_build_experimental/v4l/as3645a.o
  CC [M]  /usr/src/media_build_experimental/v4l/lm3560.o
  CC [M]  /usr/src/media_build_experimental/v4l/lm3646.o
  CC [M]  /usr/src/media_build_experimental/v4l/smiapp-pll.o
  CC [M]  /usr/src/media_build_experimental/v4l/ak881x.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-kbd-i2c.o
  CC [M]  /usr/src/media_build_experimental/v4l/ml86v7667.o
  CC [M]  /usr/src/media_build_experimental/v4l/tuner-xc2028.o
  CC [M]  /usr/src/media_build_experimental/v4l/tuner-simple.o
  CC [M]  /usr/src/media_build_experimental/v4l/tuner-types.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt20xx.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda8290.o
  CC [M]  /usr/src/media_build_experimental/v4l/tea5767.o
  CC [M]  /usr/src/media_build_experimental/v4l/tea5761.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda9887.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda827x.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda18271.o
  CC [M]  /usr/src/media_build_experimental/v4l/xc5000.o
  CC [M]  /usr/src/media_build_experimental/v4l/xc4000.o
  CC [M]  /usr/src/media_build_experimental/v4l/msi001.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt2060.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt2063.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt2266.o
  CC [M]  /usr/src/media_build_experimental/v4l/qt1010.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt2131.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl5005s.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl5007t.o
  CC [M]  /usr/src/media_build_experimental/v4l/mc44s803.o
  CC [M]  /usr/src/media_build_experimental/v4l/max2165.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18218.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18212.o
  CC [M]  /usr/src/media_build_experimental/v4l/e4000.o
  CC [M]  /usr/src/media_build_experimental/v4l/fc2580.o
  CC [M]  /usr/src/media_build_experimental/v4l/tua9001.o
  CC [M]  /usr/src/media_build_experimental/v4l/si2157.o
  CC [M]  /usr/src/media_build_experimental/v4l/m88ts2022.o
  CC [M]  /usr/src/media_build_experimental/v4l/fc0011.o
  CC [M]  /usr/src/media_build_experimental/v4l/fc0012.o
  CC [M]  /usr/src/media_build_experimental/v4l/fc0013.o
  CC [M]  /usr/src/media_build_experimental/v4l/it913x.o
  CC [M]  /usr/src/media_build_experimental/v4l/r820t.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl301rf.o
  CC [M]  /usr/src/media_build_experimental/v4l/qm1d1c0042.o
  CC [M]  /usr/src/media_build_experimental/v4l/m88rs6000t.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-pll.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0299.o
  LD [M]  /usr/src/media_build_experimental/v4l/stb0899.o
  CC [M]  /usr/src/media_build_experimental/v4l/stb6100.o
  CC [M]  /usr/src/media_build_experimental/v4l/sp8870.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx22700.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5h1432.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx24110.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda8083.o
  CC [M]  /usr/src/media_build_experimental/v4l/l64781.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib3000mb.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib3000mc.o
  CC [M]  /usr/src/media_build_experimental/v4l/dibx000_common.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib7000m.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib7000p.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib8000.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib9000.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt312.o
  CC [M]  /usr/src/media_build_experimental/v4l/ves1820.o
  CC [M]  /usr/src/media_build_experimental/v4l/ves1x93.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda1004x.o
  CC [M]  /usr/src/media_build_experimental/v4l/sp887x.o
  CC [M]  /usr/src/media_build_experimental/v4l/nxt6000.o
  CC [M]  /usr/src/media_build_experimental/v4l/mt352.o
  CC [M]  /usr/src/media_build_experimental/v4l/zl10036.o
  CC [M]  /usr/src/media_build_experimental/v4l/zl10039.o
  CC [M]  /usr/src/media_build_experimental/v4l/zl10353.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx22702.o
  LD [M]  /usr/src/media_build_experimental/v4l/drxd.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda10021.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda10023.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0297.o
  CC [M]  /usr/src/media_build_experimental/v4l/nxt200x.o
  CC [M]  /usr/src/media_build_experimental/v4l/or51211.o
  CC [M]  /usr/src/media_build_experimental/v4l/or51132.o
  CC [M]  /usr/src/media_build_experimental/v4l/bcm3510.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5h1420.o
  CC [M]  /usr/src/media_build_experimental/v4l/lgdt330x.o
  CC [M]  /usr/src/media_build_experimental/v4l/lgdt3305.o
  CC [M]  /usr/src/media_build_experimental/v4l/lg2160.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx24123.o
  CC [M]  /usr/src/media_build_experimental/v4l/lnbp21.o
  CC [M]  /usr/src/media_build_experimental/v4l/lnbp22.o
  CC [M]  /usr/src/media_build_experimental/v4l/isl6405.o
  CC [M]  /usr/src/media_build_experimental/v4l/isl6421.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda10086.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda826x.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda8261.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib0070.o
  CC [M]  /usr/src/media_build_experimental/v4l/dib0090.o
  CC [M]  /usr/src/media_build_experimental/v4l/tua6100.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5h1409.o
  CC [M]  /usr/src/media_build_experimental/v4l/itd1000.o
  CC [M]  /usr/src/media_build_experimental/v4l/au8522_common.o
  CC [M]  /usr/src/media_build_experimental/v4l/au8522_dig.o
  CC [M]  /usr/src/media_build_experimental/v4l/au8522_decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda10048.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx24113.o
  CC [M]  /usr/src/media_build_experimental/v4l/s5h1411.o
  CC [M]  /usr/src/media_build_experimental/v4l/lgs8gl5.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda665x.o
  CC [M]  /usr/src/media_build_experimental/v4l/lgs8gxx.o
  CC [M]  /usr/src/media_build_experimental/v4l/atbm8830.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb_dummy_fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9013.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx24116.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx24117.o
  CC [M]  /usr/src/media_build_experimental/v4l/si21xx.o
  CC [M]  /usr/src/media_build_experimental/v4l/si2168.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0288.o
  CC [M]  /usr/src/media_build_experimental/v4l/stb6000.o
  CC [M]  /usr/src/media_build_experimental/v4l/s921.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv6110.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0900.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv090x.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv6110x.o
  CC [M]  /usr/src/media_build_experimental/v4l/m88ds3103.o
  CC [M]  /usr/src/media_build_experimental/v4l/isl6423.o
  CC [M]  /usr/src/media_build_experimental/v4l/ec100.o
  CC [M]  /usr/src/media_build_experimental/v4l/hd29l2.o
  CC [M]  /usr/src/media_build_experimental/v4l/ds3000.o
  CC [M]  /usr/src/media_build_experimental/v4l/ts2020.o
  CC [M]  /usr/src/media_build_experimental/v4l/mb86a16.o
  LD [M]  /usr/src/media_build_experimental/v4l/drx39xyj.o
  CC [M]  /usr/src/media_build_experimental/v4l/mb86a20s.o
  CC [M]  /usr/src/media_build_experimental/v4l/ix2505v.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0367.o
  LD [M]  /usr/src/media_build_experimental/v4l/cxd2820r.o
  LD [M]  /usr/src/media_build_experimental/v4l/drxk.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18271c2dd.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0367dd.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda18212dd.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxd2843.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv0910.o
  CC [M]  /usr/src/media_build_experimental/v4l/stv6111.o
/usr/src/media_build_experimental/v4l/stv6111.c:334:12: warning: 'AGC_Gain' defined but not used [-Wunused-variable]
 static u32 AGC_Gain[] = {
            ^
  CC [M]  /usr/src/media_build_experimental/v4l/mxl5xx.o
/usr/src/media_build_experimental/v4l/mxl5xx.c: In function 'firmware_is_alive':
/usr/src/media_build_experimental/v4l/mxl5xx.c:302:6: warning: unused variable 'status' [-Wunused-variable]
  int status;
      ^
/usr/src/media_build_experimental/v4l/mxl5xx.c: In function 'set_parameters':
/usr/src/media_build_experimental/v4l/mxl5xx.c:378:23: warning: unused variable 'demodId' [-Wunused-variable]
  MXL_HYDRA_DEMOD_ID_E demodId = state->demod;
                       ^
/usr/src/media_build_experimental/v4l/mxl5xx.c: In function 'tune':
/usr/src/media_build_experimental/v4l/mxl5xx.c:482:34: warning: unused variable 'p' [-Wunused-variable]
  struct dtv_frontend_properties *p = &fe->dtv_property_cache;
                                  ^
/usr/src/media_build_experimental/v4l/mxl5xx.c: In function 'config_ts':
/usr/src/media_build_experimental/v4l/mxl5xx.c:961:18: warning: unused variable 'mxl561_xpt_ts_valid' [-Wunused-variable]
  MXL_REG_FIELD_T mxl561_xpt_ts_valid[MXL_HYDRA_DEMOD_ID_6] = {
                  ^
/usr/src/media_build_experimental/v4l/mxl5xx.c:957:18: warning: unused variable 'mxl561_xpt_ts_sync' [-Wunused-variable]
  MXL_REG_FIELD_T mxl561_xpt_ts_sync[MXL_HYDRA_DEMOD_ID_6] = {
                  ^
/usr/src/media_build_experimental/v4l/mxl5xx.c: At top level:
/usr/src/media_build_experimental/v4l/mxl5xx.c:86:13: warning: 'le32_to_cpusn' defined but not used [-Wunused-function]
 static void le32_to_cpusn(u32 *data, u32 size)
             ^
/usr/src/media_build_experimental/v4l/mxl5xx.c:165:12: warning: 'write_register_block' defined but not used [-Wunused-function]
 static int write_register_block(struct mxl *state, u32 reg, u32 size, u8 *data)
            ^
/usr/src/media_build_experimental/v4l/mxl5xx.c:234:12: warning: 'read_register_block' defined but not used [-Wunused-function]
 static int read_register_block(struct mxl *state, u32 reg, u32 size, u8 *data)
            ^
/usr/src/media_build_experimental/v4l/mxl5xx.c:289:13: warning: 'extract_from_mnemonic' defined but not used [-Wunused-function]
 static void extract_from_mnemonic(u32 regAddr, u8 lsbPos, u8 width,
             ^
/usr/src/media_build_experimental/v4l/mxl5xx.c:338:12: warning: 'cfg_scrambler' defined but not used [-Wunused-function]
 static int cfg_scrambler(struct mxl *state)
            ^
  CC [M]  /usr/src/media_build_experimental/v4l/si2165.o
  CC [M]  /usr/src/media_build_experimental/v4l/a8293.o
  CC [M]  /usr/src/media_build_experimental/v4l/sp2.o
  CC [M]  /usr/src/media_build_experimental/v4l/tda10071.o
  CC [M]  /usr/src/media_build_experimental/v4l/rtl2830.o
  CC [M]  /usr/src/media_build_experimental/v4l/rtl2832.o
  CC [M]  /usr/src/media_build_experimental/v4l/rtl2832_sdr.o
  CC [M]  /usr/src/media_build_experimental/v4l/m88rs2000.o
  CC [M]  /usr/src/media_build_experimental/v4l/af9033.o
  CC [M]  /usr/src/media_build_experimental/v4l/as102_fe.o
  CC [M]  /usr/src/media_build_experimental/v4l/tc90522.o
  LD [M]  /usr/src/media_build_experimental/v4l/media.o
  LD [M]  /usr/src/media_build_experimental/v4l/videodev.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-common.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-dv-timings.o
  LD [M]  /usr/src/media_build_experimental/v4l/tuner.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-mem2mem.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf-dma-sg.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf-dma-contig.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf-vmalloc.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf2-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf2-memops.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf2-vmalloc.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf2-dma-contig.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf2-dma-sg.o
  CC [M]  /usr/src/media_build_experimental/v4l/videobuf2-dvb.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-adstech-dvb-t-pci.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-alink-dtu-m.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-anysee.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-apac-viewcomp.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-asus-pc39.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-asus-ps3-100.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-ati-tv-wonder-hd-600.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-ati-x10.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-a16d.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-cardbus.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-dvbt.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-m135a.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-m733a-rm-k6.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-rm-ks.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-avertv-303.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-azurewave-ad-tu700.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-behold.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-behold-columbus.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-budget-ci-old.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-cinergy-1400.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-cinergy.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-delock-61959.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-dib0700-nec.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-dib0700-rc5.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-digitalnow-tinytwin.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-digittrade.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-dm1105-nec.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-dntv-live-dvb-t.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-dntv-live-dvbt-pro.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-dvbsky.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-em-terratec.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-encore-enltv2.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-encore-enltv.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-encore-enltv-fm53.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-evga-indtube.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-eztv.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-flydvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-flyvideo.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-fusionhdtv-mce.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-gadmei-rm008z.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-genius-tvgo-a11mce.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-gotview7135.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-imon-mce.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-imon-pad.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-iodata-bctv7e.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-it913x-v1.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-it913x-v2.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-kaiomy.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-kworld-315u.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-kworld-pc150u.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-kworld-plus-tv-analog.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-leadtek-y04g0051.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-lirc.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-lme2510.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-manli.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-medion-x10.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-medion-x10-digitainer.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-medion-x10-or2x.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-msi-digivox-ii.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-msi-digivox-iii.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-msi-tvanywhere.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-msi-tvanywhere-plus.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-nebula.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-nec-terratec-cinergy-xs.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-norwood.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-npgtech.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pctv-sedna.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pinnacle-color.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pinnacle-grey.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pinnacle-pctv-hd.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pixelview.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pixelview-mk12.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pixelview-002t.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pixelview-new.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-powercolor-real-angel.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-proteus-2309.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-purpletv.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-pv951.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-hauppauge.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-rc6-mce.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-real-audio-220-32-keys.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-reddo.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-snapstream-firefly.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-streamzap.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-tbs-nec.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-technisat-usb2.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-terratec-cinergy-xs.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-terratec-slim.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-terratec-slim-2.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-tevii-nec.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-tivo.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-total-media-in-hand.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-total-media-in-hand-02.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-trekstor.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-tt-1500.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-twinhan1027.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-videomate-m1f.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-videomate-s350.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-videomate-tv-pvr.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-winfast.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-winfast-usbii-deluxe.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-su3000.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_dev.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-nec-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-rc5-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-rc6-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-jvc-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-sony-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-sanyo-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-sharp-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-mce_kbd-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-lirc-codec.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-xmp-decoder.o
  CC [M]  /usr/src/media_build_experimental/v4l/ati_remote.o
  CC [M]  /usr/src/media_build_experimental/v4l/ir-hix5hd2.o
  CC [M]  /usr/src/media_build_experimental/v4l/imon.o
  CC [M]  /usr/src/media_build_experimental/v4l/ite-cir.o
  CC [M]  /usr/src/media_build_experimental/v4l/mceusb.o
  CC [M]  /usr/src/media_build_experimental/v4l/fintek-cir.o
  CC [M]  /usr/src/media_build_experimental/v4l/nuvoton-cir.o
  CC [M]  /usr/src/media_build_experimental/v4l/ene_ir.o
  CC [M]  /usr/src/media_build_experimental/v4l/redrat3.o
  CC [M]  /usr/src/media_build_experimental/v4l/streamzap.o
  CC [M]  /usr/src/media_build_experimental/v4l/winbond-cir.o
  CC [M]  /usr/src/media_build_experimental/v4l/rc-loopback.o
  CC [M]  /usr/src/media_build_experimental/v4l/gpio-ir-recv.o
  CC [M]  /usr/src/media_build_experimental/v4l/igorplugusb.o
  CC [M]  /usr/src/media_build_experimental/v4l/iguanair.o
  CC [M]  /usr/src/media_build_experimental/v4l/ttusbir.o
  LD [M]  /usr/src/media_build_experimental/v4l/img-ir.o
  LD [M]  /usr/src/media_build_experimental/v4l/b2c2-flexcop.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7146.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7146_vv.o
  LD [M]  /usr/src/media_build_experimental/v4l/smsmdtv.o
  LD [M]  /usr/src/media_build_experimental/v4l/smsdvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx2341x.o
  CC [M]  /usr/src/media_build_experimental/v4l/btcx-risc.o
  CC [M]  /usr/src/media_build_experimental/v4l/tveeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/cypress_firmware.o
  CC [M]  /usr/src/media_build_experimental/v4l/timblogiw.o
  CC [M]  /usr/src/media_build_experimental/v4l/via-camera.o
  LD [M]  /usr/src/media_build_experimental/v4l/cafe_ccic.o
  LD [M]  /usr/src/media_build_experimental/v4l/vivid.o
  CC [M]  /usr/src/media_build_experimental/v4l/vim2m.o
  CC [M]  /usr/src/media_build_experimental/v4l/sh_veu.o
  CC [M]  /usr/src/media_build_experimental/v4l/m2m-deinterlace.o
  CC [M]  /usr/src/media_build_experimental/v4l/soc_camera.o
  CC [M]  /usr/src/media_build_experimental/v4l/soc_mediabus.o
  CC [M]  /usr/src/media_build_experimental/v4l/soc_scale_crop.o
  CC [M]  /usr/src/media_build_experimental/v4l/soc_camera_platform.o
  CC [M]  /usr/src/media_build_experimental/v4l/ttpci-eeprom.o
  CC [M]  /usr/src/media_build_experimental/v4l/budget-core.o
  CC [M]  /usr/src/media_build_experimental/v4l/budget.o
  CC [M]  /usr/src/media_build_experimental/v4l/budget-av.o
  CC [M]  /usr/src/media_build_experimental/v4l/budget-ci.o
  CC [M]  /usr/src/media_build_experimental/v4l/budget-patch.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-ttpci.o
  LD [M]  /usr/src/media_build_experimental/v4l/b2c2-flexcop-pci.o
  CC [M]  /usr/src/media_build_experimental/v4l/pluto2.o
  CC [M]  /usr/src/media_build_experimental/v4l/dm1105.o
  LD [M]  /usr/src/media_build_experimental/v4l/earth-pt1.o
  LD [M]  /usr/src/media_build_experimental/v4l/earth-pt3.o
  LD [M]  /usr/src/media_build_experimental/v4l/mantis_core.o
  LD [M]  /usr/src/media_build_experimental/v4l/mantis.o
  LD [M]  /usr/src/media_build_experimental/v4l/hopper.o
  LD [M]  /usr/src/media_build_experimental/v4l/ngene.o
  CC [M]  /usr/src/media_build_experimental/v4l/ddbridge.o
In file included from /usr/src/media_build_experimental/v4l/ddbridge-core.c:53:0,
                 from /usr/src/media_build_experimental/v4l/ddbridge.c:47:
/usr/src/media_build_experimental/v4l/ddbridge-i2c.c: In function 'ddb_i2c_master_xfer':
/usr/src/media_build_experimental/v4l/ddbridge-i2c.c:140:6: warning: unused variable 'i2c_buf' [-Wunused-variable]
  u32 i2c_buf = dev->info->regmap->i2c_buf->base;
      ^
In file included from /usr/src/media_build_experimental/v4l/ddbridge.c:47:0:
/usr/src/media_build_experimental/v4l/ddbridge-core.c: In function 'ddb_input_start':
/usr/src/media_build_experimental/v4l/ddbridge-core.c:402:6: warning: unused variable 'tsbase' [-Wunused-variable]
  u32 tsbase = TS_INPUT_BASE + input->nr * 0x10; 
      ^
/usr/src/media_build_experimental/v4l/ddbridge-core.c: In function 'gtl_link_handler':
/usr/src/media_build_experimental/v4l/ddbridge-core.c:4215:14: warning: unused variable 'dev' [-Wunused-variable]
  struct ddb *dev = (struct ddb *) priv;
              ^
/usr/src/media_build_experimental/v4l/ddbridge-core.c: In function 'gtl_irq_handler':
/usr/src/media_build_experimental/v4l/ddbridge-core.c:4222:14: warning: unused variable 'dev' [-Wunused-variable]
  struct ddb *dev = (struct ddb *) priv;
              ^
/usr/src/media_build_experimental/v4l/ddbridge.c: At top level:
/usr/src/media_build_experimental/v4l/ddbridge.c:267:26: warning: 'octopus_i2c_2' defined but not used [-Wunused-variable]
 static struct ddb_regset octopus_i2c_2 = {
                          ^
  LD [M]  /usr/src/media_build_experimental/v4l/saa716x_core.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_budget.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa716x_hybrid.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa716x_ff.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxb.o
  CC [M]  /usr/src/media_build_experimental/v4l/hexium_orion.o
  CC [M]  /usr/src/media_build_experimental/v4l/hexium_gemini.o
  CC [M]  /usr/src/media_build_experimental/v4l/smipcie.o
  LD [M]  /usr/src/media_build_experimental/v4l/ivtv.o
  LD [M]  /usr/src/media_build_experimental/v4l/ivtv-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/ivtvfb.o
  LD [M]  /usr/src/media_build_experimental/v4l/zr36067.o
  CC [M]  /usr/src/media_build_experimental/v4l/videocodec.o
  CC [M]  /usr/src/media_build_experimental/v4l/zr36050.o
  CC [M]  /usr/src/media_build_experimental/v4l/zr36016.o
  CC [M]  /usr/src/media_build_experimental/v4l/zr36060.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx18.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx18-alsa.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx23885.o
  CC [M]  /usr/src/media_build_experimental/v4l/altera-ci.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx25821.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx25821-alsa.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx88xx.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx8800.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx8802.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-blackbird.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-dvb.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx88-vp3054-i2c.o
  LD [M]  /usr/src/media_build_experimental/v4l/bttv.o
  CC [M]  /usr/src/media_build_experimental/v4l/bt878.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-bt8xx.o
  CC [M]  /usr/src/media_build_experimental/v4l/dst.o
  CC [M]  /usr/src/media_build_experimental/v4l/dst_ca.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7134.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-empress.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-go7007.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7134-dvb.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7164.o
  LD [M]  /usr/src/media_build_experimental/v4l/tw68.o
  CC [M]  /usr/src/media_build_experimental/v4l/meye.o
  LD [M]  /usr/src/media_build_experimental/v4l/solo6x10.o
  CC [M]  /usr/src/media_build_experimental/v4l/ttusb_dec.o
  CC [M]  /usr/src/media_build_experimental/v4l/ttusbdecfe.o
  CC [M]  /usr/src/media_build_experimental/v4l/dvb-ttusb-budget.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-vp7045.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-vp702x.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-gp8psk.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dtt200u.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-common.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-a800.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-mb.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-mc.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-nova-t-usb2.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-umt-010.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-m920x.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-digitv.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-cxusb.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-ttusb2.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dib0700.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-opera.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9005.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9005-remote.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-pctv452e.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dw2102.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dtv5100.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-cinergyT2.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-friio.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-az6027.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-technisat-usb2.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb_usb_v2.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9015.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9035.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-anysee.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-au6610.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-az6007.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-ce6230.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-ec168.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-lmedm04.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-gl861.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-mxl111sf.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl111sf-demod.o
  CC [M]  /usr/src/media_build_experimental/v4l/mxl111sf-tuner.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-rtl28xxu.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dvbsky.o
  CC [M]  /usr/src/media_build_experimental/v4l/smsusb.o
  LD [M]  /usr/src/media_build_experimental/v4l/b2c2-flexcop-usb.o
  CC [M]  /usr/src/media_build_experimental/v4l/zr364xx.o
  LD [M]  /usr/src/media_build_experimental/v4l/stkwebcam.o
  CC [M]  /usr/src/media_build_experimental/v4l/s2255drv.o
  LD [M]  /usr/src/media_build_experimental/v4l/uvcvideo.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_main.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_benq.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_conex.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_cpia1.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_dtcs033.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_etoms.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_finepix.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_jeilinj.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_jl2005bcd.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_kinect.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_konica.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_mars.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_mr97310a.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_nw80x.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_ov519.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_ov534.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_ov534_9.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_pac207.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_pac7302.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_pac7311.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_se401.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sn9c2028.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sn9c20x.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sonixb.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sonixj.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca500.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca501.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca505.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca506.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca508.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca561.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca1528.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sq905.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sq905c.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sq930x.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sunplus.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stk014.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stk1135.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stv0680.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_t613.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_topro.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_tv8532.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_vc032x.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_vicam.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_xirlink_cit.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_zc3xx.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_m5602.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stv06xx.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_gl860.o
  LD [M]  /usr/src/media_build_experimental/v4l/pwc.o
  CC [M]  /usr/src/media_build_experimental/v4l/airspy.o
  CC [M]  /usr/src/media_build_experimental/v4l/hackrf.o
  CC [M]  /usr/src/media_build_experimental/v4l/msi2500.o
  LD [M]  /usr/src/media_build_experimental/v4l/cpia2.o
  LD [M]  /usr/src/media_build_experimental/v4l/au0828.o
  LD [M]  /usr/src/media_build_experimental/v4l/hdpvr.o
  LD [M]  /usr/src/media_build_experimental/v4l/pvrusb2.o
  LD [M]  /usr/src/media_build_experimental/v4l/poseidon.o
  LD [M]  /usr/src/media_build_experimental/v4l/usbvision.o
  LD [M]  /usr/src/media_build_experimental/v4l/stk1160.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx231xx.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx231xx-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/cx231xx-dvb.o
  LD [M]  /usr/src/media_build_experimental/v4l/tm6000.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/tm6000-dvb.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-v4l.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-alsa.o
  CC [M]  /usr/src/media_build_experimental/v4l/em28xx-dvb.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-rc.o
  LD [M]  /usr/src/media_build_experimental/v4l/usbtv.o
  LD [M]  /usr/src/media_build_experimental/v4l/go7007.o
  CC [M]  /usr/src/media_build_experimental/v4l/go7007-usb.o
  CC [M]  /usr/src/media_build_experimental/v4l/go7007-loader.o
  LD [M]  /usr/src/media_build_experimental/v4l/s2250.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-as102.o
  CC [M]  /usr/src/media_build_experimental/v4l/smssdio.o
  LD [M]  /usr/src/media_build_experimental/v4l/firedtv.o
  CC [M]  /usr/src/media_build_experimental/v4l/c-qcam.o
  CC [M]  /usr/src/media_build_experimental/v4l/bw-qcam.o
  CC [M]  /usr/src/media_build_experimental/v4l/w9966.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-maxiradio.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-shark.o
  LD [M]  /usr/src/media_build_experimental/v4l/shark2.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-si476x.o
  CC [M]  /usr/src/media_build_experimental/v4l/dsbr100.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-usb-si470x.o
  CC [M]  /usr/src/media_build_experimental/v4l/si4713.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-usb-si4713.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-platform-si4713.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-mr800.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-keene.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-ma901.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-tea5764.o
  CC [M]  /usr/src/media_build_experimental/v4l/saa7706h.o
  CC [M]  /usr/src/media_build_experimental/v4l/tef6862.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-timb.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-wl1273.o
  LD [M]  /usr/src/media_build_experimental/v4l/fm_drv.o
  CC [M]  /usr/src/media_build_experimental/v4l/tea575x.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-raremono.o
  CC [M]  /usr/src/media_build_experimental/v4l/radio-bcm2048.o
  CC [M]  /usr/src/media_build_experimental/v4l/cxd2099.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_bt829.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_imon.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_parallel.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_sasem.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_serial.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_sir.o
  CC [M]  /usr/src/media_build_experimental/v4l/lirc_zilog.o
  CC [M]  /usr/src/media_build_experimental/v4l/dt3155v4l.o
  CC [M]  /usr/src/media_build_experimental/v4l/tcm825x.o
  CC [M]  /usr/src/media_build_experimental/v4l/v4l2-int-device.o
  LD [M]  /usr/src/media_build_experimental/v4l/altera-stapl.o
  LD [M]  /usr/src/media_build_experimental/v4l/snd-bt87x.o
  Building modules, stage 2.
  MODPOST 630 modules
  CC      /usr/src/media_build_experimental/v4l/a8293.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/a8293.ko
  CC      /usr/src/media_build_experimental/v4l/ad9389b.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ad9389b.ko
  CC      /usr/src/media_build_experimental/v4l/adp1653.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adp1653.ko
  CC      /usr/src/media_build_experimental/v4l/adv7170.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7170.ko
  CC      /usr/src/media_build_experimental/v4l/adv7175.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7175.ko
  CC      /usr/src/media_build_experimental/v4l/adv7180.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7180.ko
  CC      /usr/src/media_build_experimental/v4l/adv7183.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7183.ko
  CC      /usr/src/media_build_experimental/v4l/adv7343.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7343.ko
  CC      /usr/src/media_build_experimental/v4l/adv7393.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7393.ko
  CC      /usr/src/media_build_experimental/v4l/adv7511.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7511.ko
  CC      /usr/src/media_build_experimental/v4l/adv7604.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7604.ko
  CC      /usr/src/media_build_experimental/v4l/adv7842.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/adv7842.ko
  CC      /usr/src/media_build_experimental/v4l/af9013.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/af9013.ko
  CC      /usr/src/media_build_experimental/v4l/af9033.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/af9033.ko
  CC      /usr/src/media_build_experimental/v4l/airspy.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/airspy.ko
  CC      /usr/src/media_build_experimental/v4l/ak881x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ak881x.ko
  CC      /usr/src/media_build_experimental/v4l/altera-ci.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/altera-ci.ko
  CC      /usr/src/media_build_experimental/v4l/altera-stapl.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/altera-stapl.ko
  CC      /usr/src/media_build_experimental/v4l/aptina-pll.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/aptina-pll.ko
  CC      /usr/src/media_build_experimental/v4l/as102_fe.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/as102_fe.ko
  CC      /usr/src/media_build_experimental/v4l/as3645a.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/as3645a.ko
  CC      /usr/src/media_build_experimental/v4l/atbm8830.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/atbm8830.ko
  CC      /usr/src/media_build_experimental/v4l/ati_remote.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ati_remote.ko
  CC      /usr/src/media_build_experimental/v4l/au0828.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/au0828.ko
  CC      /usr/src/media_build_experimental/v4l/au8522_common.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/au8522_common.ko
  CC      /usr/src/media_build_experimental/v4l/au8522_decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/au8522_decoder.ko
  CC      /usr/src/media_build_experimental/v4l/au8522_dig.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/au8522_dig.ko
  CC      /usr/src/media_build_experimental/v4l/b2c2-flexcop-pci.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/b2c2-flexcop-pci.ko
  CC      /usr/src/media_build_experimental/v4l/b2c2-flexcop-usb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/b2c2-flexcop-usb.ko
  CC      /usr/src/media_build_experimental/v4l/b2c2-flexcop.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/b2c2-flexcop.ko
  CC      /usr/src/media_build_experimental/v4l/bcm3510.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bcm3510.ko
  CC      /usr/src/media_build_experimental/v4l/bt819.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bt819.ko
  CC      /usr/src/media_build_experimental/v4l/bt856.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bt856.ko
  CC      /usr/src/media_build_experimental/v4l/bt866.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bt866.ko
  CC      /usr/src/media_build_experimental/v4l/bt878.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bt878.ko
  CC      /usr/src/media_build_experimental/v4l/btcx-risc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/btcx-risc.ko
  CC      /usr/src/media_build_experimental/v4l/bttv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bttv.ko
  CC      /usr/src/media_build_experimental/v4l/budget-av.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/budget-av.ko
  CC      /usr/src/media_build_experimental/v4l/budget-ci.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/budget-ci.ko
  CC      /usr/src/media_build_experimental/v4l/budget-core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/budget-core.ko
  CC      /usr/src/media_build_experimental/v4l/budget-patch.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/budget-patch.ko
  CC      /usr/src/media_build_experimental/v4l/budget.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/budget.ko
  CC      /usr/src/media_build_experimental/v4l/bw-qcam.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/bw-qcam.ko
  CC      /usr/src/media_build_experimental/v4l/c-qcam.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/c-qcam.ko
  CC      /usr/src/media_build_experimental/v4l/cafe_ccic.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cafe_ccic.ko
  CC      /usr/src/media_build_experimental/v4l/cpia2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cpia2.ko
  CC      /usr/src/media_build_experimental/v4l/cs5345.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cs5345.ko
  CC      /usr/src/media_build_experimental/v4l/cs53l32a.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cs53l32a.ko
  CC      /usr/src/media_build_experimental/v4l/cx18-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx18-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/cx18.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx18.ko
  CC      /usr/src/media_build_experimental/v4l/cx22700.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx22700.ko
  CC      /usr/src/media_build_experimental/v4l/cx22702.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx22702.ko
  CC      /usr/src/media_build_experimental/v4l/cx231xx-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx231xx-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/cx231xx-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx231xx-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/cx231xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx231xx.ko
  CC      /usr/src/media_build_experimental/v4l/cx2341x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx2341x.ko
  CC      /usr/src/media_build_experimental/v4l/cx23885.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx23885.ko
  CC      /usr/src/media_build_experimental/v4l/cx24110.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx24110.ko
  CC      /usr/src/media_build_experimental/v4l/cx24113.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx24113.ko
  CC      /usr/src/media_build_experimental/v4l/cx24116.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx24116.ko
  CC      /usr/src/media_build_experimental/v4l/cx24117.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx24117.ko
  CC      /usr/src/media_build_experimental/v4l/cx24123.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx24123.ko
  CC      /usr/src/media_build_experimental/v4l/cx25821-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx25821-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/cx25821.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx25821.ko
  CC      /usr/src/media_build_experimental/v4l/cx25840.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx25840.ko
  CC      /usr/src/media_build_experimental/v4l/cx88-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx88-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/cx88-blackbird.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx88-blackbird.ko
  CC      /usr/src/media_build_experimental/v4l/cx88-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx88-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/cx88-vp3054-i2c.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx88-vp3054-i2c.ko
  CC      /usr/src/media_build_experimental/v4l/cx8800.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx8800.ko
  CC      /usr/src/media_build_experimental/v4l/cx8802.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx8802.ko
  CC      /usr/src/media_build_experimental/v4l/cx88xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cx88xx.ko
  CC      /usr/src/media_build_experimental/v4l/cxd2099.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cxd2099.ko
  CC      /usr/src/media_build_experimental/v4l/cxd2820r.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cxd2820r.ko
  CC      /usr/src/media_build_experimental/v4l/cxd2843.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cxd2843.ko
  CC      /usr/src/media_build_experimental/v4l/cypress_firmware.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/cypress_firmware.ko
  CC      /usr/src/media_build_experimental/v4l/ddbridge.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ddbridge.ko
  CC      /usr/src/media_build_experimental/v4l/dib0070.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib0070.ko
  CC      /usr/src/media_build_experimental/v4l/dib0090.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib0090.ko
  CC      /usr/src/media_build_experimental/v4l/dib3000mb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib3000mb.ko
  CC      /usr/src/media_build_experimental/v4l/dib3000mc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib3000mc.ko
  CC      /usr/src/media_build_experimental/v4l/dib7000m.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib7000m.ko
  CC      /usr/src/media_build_experimental/v4l/dib7000p.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib7000p.ko
  CC      /usr/src/media_build_experimental/v4l/dib8000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib8000.ko
  CC      /usr/src/media_build_experimental/v4l/dib9000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dib9000.ko
  CC      /usr/src/media_build_experimental/v4l/dibx000_common.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dibx000_common.ko
  CC      /usr/src/media_build_experimental/v4l/dm1105.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dm1105.ko
  CC      /usr/src/media_build_experimental/v4l/drx39xyj.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/drx39xyj.ko
  CC      /usr/src/media_build_experimental/v4l/drxd.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/drxd.ko
  CC      /usr/src/media_build_experimental/v4l/drxk.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/drxk.ko
  CC      /usr/src/media_build_experimental/v4l/ds3000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ds3000.ko
  CC      /usr/src/media_build_experimental/v4l/dsbr100.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dsbr100.ko
  CC      /usr/src/media_build_experimental/v4l/dst.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dst.ko
  CC      /usr/src/media_build_experimental/v4l/dst_ca.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dst_ca.ko
  CC      /usr/src/media_build_experimental/v4l/dt3155v4l.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dt3155v4l.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-as102.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-as102.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-bt8xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-bt8xx.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-core.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-pll.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-pll.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-ttpci.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-ttpci.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-ttusb-budget.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-ttusb-budget.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-a800.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-a800.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-af9005-remote.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9005-remote.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-af9005.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9005.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-af9015.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9015.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-af9035.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-af9035.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-anysee.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-anysee.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-au6610.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-au6610.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-az6007.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-az6007.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-az6027.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-az6027.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-ce6230.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-ce6230.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-cinergyT2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-cinergyT2.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-cxusb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-cxusb.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dib0700.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dib0700.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-common.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-common.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-mb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-mb.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-mc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dibusb-mc.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-digitv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-digitv.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dtt200u.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dtt200u.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dtv5100.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dtv5100.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dvbsky.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dvbsky.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-dw2102.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-dw2102.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-ec168.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-ec168.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-friio.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-friio.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-gl861.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-gl861.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-gp8psk.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-gp8psk.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-lmedm04.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-lmedm04.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-m920x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-m920x.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-mxl111sf.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-mxl111sf.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-nova-t-usb2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-nova-t-usb2.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-opera.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-opera.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-pctv452e.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-pctv452e.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-rtl28xxu.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-rtl28xxu.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-technisat-usb2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-technisat-usb2.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-ttusb2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-ttusb2.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-umt-010.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-umt-010.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-vp702x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-vp702x.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb-vp7045.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb-vp7045.ko
  CC      /usr/src/media_build_experimental/v4l/dvb-usb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb-usb.ko
  CC      /usr/src/media_build_experimental/v4l/dvb_dummy_fe.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb_dummy_fe.ko
  CC      /usr/src/media_build_experimental/v4l/dvb_usb_v2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/dvb_usb_v2.ko
  CC      /usr/src/media_build_experimental/v4l/e4000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/e4000.ko
  CC      /usr/src/media_build_experimental/v4l/earth-pt1.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/earth-pt1.ko
  CC      /usr/src/media_build_experimental/v4l/earth-pt3.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/earth-pt3.ko
  CC      /usr/src/media_build_experimental/v4l/ec100.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ec100.ko
  CC      /usr/src/media_build_experimental/v4l/em28xx-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/em28xx-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/em28xx-rc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-rc.ko
  CC      /usr/src/media_build_experimental/v4l/em28xx-v4l.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx-v4l.ko
  CC      /usr/src/media_build_experimental/v4l/em28xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/em28xx.ko
  CC      /usr/src/media_build_experimental/v4l/ene_ir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ene_ir.ko
  CC      /usr/src/media_build_experimental/v4l/fc0011.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/fc0011.ko
  CC      /usr/src/media_build_experimental/v4l/fc0012.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/fc0012.ko
  CC      /usr/src/media_build_experimental/v4l/fc0013.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/fc0013.ko
  CC      /usr/src/media_build_experimental/v4l/fc2580.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/fc2580.ko
  CC      /usr/src/media_build_experimental/v4l/fintek-cir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/fintek-cir.ko
  CC      /usr/src/media_build_experimental/v4l/firedtv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/firedtv.ko
  CC      /usr/src/media_build_experimental/v4l/fm_drv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/fm_drv.ko
  CC      /usr/src/media_build_experimental/v4l/go7007-loader.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/go7007-loader.ko
  CC      /usr/src/media_build_experimental/v4l/go7007-usb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/go7007-usb.ko
  CC      /usr/src/media_build_experimental/v4l/go7007.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/go7007.ko
  CC      /usr/src/media_build_experimental/v4l/gpio-ir-recv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gpio-ir-recv.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_benq.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_benq.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_conex.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_conex.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_cpia1.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_cpia1.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_dtcs033.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_dtcs033.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_etoms.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_etoms.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_finepix.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_finepix.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_gl860.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_gl860.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_jeilinj.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_jeilinj.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_jl2005bcd.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_jl2005bcd.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_kinect.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_kinect.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_konica.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_konica.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_m5602.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_m5602.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_main.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_main.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_mars.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_mars.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_mr97310a.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_mr97310a.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_nw80x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_nw80x.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_ov519.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_ov519.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_ov534.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_ov534.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_ov534_9.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_ov534_9.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_pac207.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_pac207.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_pac7302.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_pac7302.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_pac7311.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_pac7311.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_se401.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_se401.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sn9c2028.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sn9c2028.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sn9c20x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sn9c20x.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sonixb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sonixb.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sonixj.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sonixj.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca1528.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca1528.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca500.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca500.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca501.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca501.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca505.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca505.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca506.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca506.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca508.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca508.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_spca561.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_spca561.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sq905.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sq905.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sq905c.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sq905c.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sq930x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sq930x.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_stk014.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stk014.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_stk1135.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stk1135.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_stv0680.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stv0680.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_stv06xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_stv06xx.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_sunplus.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_sunplus.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_t613.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_t613.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_topro.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_topro.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_tv8532.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_tv8532.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_vc032x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_vc032x.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_vicam.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_vicam.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_xirlink_cit.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_xirlink_cit.ko
  CC      /usr/src/media_build_experimental/v4l/gspca_zc3xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/gspca_zc3xx.ko
  CC      /usr/src/media_build_experimental/v4l/hackrf.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/hackrf.ko
  CC      /usr/src/media_build_experimental/v4l/hd29l2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/hd29l2.ko
  CC      /usr/src/media_build_experimental/v4l/hdpvr.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/hdpvr.ko
  CC      /usr/src/media_build_experimental/v4l/hexium_gemini.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/hexium_gemini.ko
  CC      /usr/src/media_build_experimental/v4l/hexium_orion.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/hexium_orion.ko
  CC      /usr/src/media_build_experimental/v4l/hopper.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/hopper.ko
  CC      /usr/src/media_build_experimental/v4l/igorplugusb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/igorplugusb.ko
  CC      /usr/src/media_build_experimental/v4l/iguanair.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/iguanair.ko
  CC      /usr/src/media_build_experimental/v4l/img-ir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/img-ir.ko
  CC      /usr/src/media_build_experimental/v4l/imon.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/imon.ko
  CC      /usr/src/media_build_experimental/v4l/imx074.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/imx074.ko
  CC      /usr/src/media_build_experimental/v4l/ir-hix5hd2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-hix5hd2.ko
  CC      /usr/src/media_build_experimental/v4l/ir-jvc-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-jvc-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-kbd-i2c.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-kbd-i2c.ko
  CC      /usr/src/media_build_experimental/v4l/ir-lirc-codec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-lirc-codec.ko
  CC      /usr/src/media_build_experimental/v4l/ir-mce_kbd-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-mce_kbd-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-nec-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-nec-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-rc5-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-rc5-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-rc6-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-rc6-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-sanyo-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-sanyo-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-sharp-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-sharp-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-sony-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-sony-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/ir-xmp-decoder.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ir-xmp-decoder.ko
  CC      /usr/src/media_build_experimental/v4l/isl6405.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/isl6405.ko
  CC      /usr/src/media_build_experimental/v4l/isl6421.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/isl6421.ko
  CC      /usr/src/media_build_experimental/v4l/isl6423.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/isl6423.ko
  CC      /usr/src/media_build_experimental/v4l/it913x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/it913x.ko
  CC      /usr/src/media_build_experimental/v4l/itd1000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/itd1000.ko
  CC      /usr/src/media_build_experimental/v4l/ite-cir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ite-cir.ko
  CC      /usr/src/media_build_experimental/v4l/ivtv-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ivtv-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/ivtv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ivtv.ko
  CC      /usr/src/media_build_experimental/v4l/ivtvfb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ivtvfb.ko
  CC      /usr/src/media_build_experimental/v4l/ix2505v.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ix2505v.ko
  CC      /usr/src/media_build_experimental/v4l/ks0127.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ks0127.ko
  CC      /usr/src/media_build_experimental/v4l/l64781.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/l64781.ko
  CC      /usr/src/media_build_experimental/v4l/lg2160.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lg2160.ko
  CC      /usr/src/media_build_experimental/v4l/lgdt3305.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lgdt3305.ko
  CC      /usr/src/media_build_experimental/v4l/lgdt330x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lgdt330x.ko
  CC      /usr/src/media_build_experimental/v4l/lgs8gl5.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lgs8gl5.ko
  CC      /usr/src/media_build_experimental/v4l/lgs8gxx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lgs8gxx.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_bt829.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_bt829.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_dev.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_dev.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_imon.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_imon.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_parallel.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_parallel.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_sasem.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_sasem.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_serial.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_serial.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_sir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_sir.ko
  CC      /usr/src/media_build_experimental/v4l/lirc_zilog.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lirc_zilog.ko
  CC      /usr/src/media_build_experimental/v4l/lm3560.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lm3560.ko
  CC      /usr/src/media_build_experimental/v4l/lm3646.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lm3646.ko
  CC      /usr/src/media_build_experimental/v4l/lnbp21.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lnbp21.ko
  CC      /usr/src/media_build_experimental/v4l/lnbp22.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/lnbp22.ko
  CC      /usr/src/media_build_experimental/v4l/m2m-deinterlace.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m2m-deinterlace.ko
  CC      /usr/src/media_build_experimental/v4l/m52790.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m52790.ko
  CC      /usr/src/media_build_experimental/v4l/m5mols.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m5mols.ko
  CC      /usr/src/media_build_experimental/v4l/m88ds3103.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m88ds3103.ko
  CC      /usr/src/media_build_experimental/v4l/m88rs2000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m88rs2000.ko
  CC      /usr/src/media_build_experimental/v4l/m88rs6000t.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m88rs6000t.ko
  CC      /usr/src/media_build_experimental/v4l/m88ts2022.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/m88ts2022.ko
  CC      /usr/src/media_build_experimental/v4l/mantis.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mantis.ko
  CC      /usr/src/media_build_experimental/v4l/mantis_core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mantis_core.ko
  CC      /usr/src/media_build_experimental/v4l/max2165.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/max2165.ko
  CC      /usr/src/media_build_experimental/v4l/mb86a16.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mb86a16.ko
  CC      /usr/src/media_build_experimental/v4l/mb86a20s.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mb86a20s.ko
  CC      /usr/src/media_build_experimental/v4l/mc44s803.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mc44s803.ko
  CC      /usr/src/media_build_experimental/v4l/mceusb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mceusb.ko
  CC      /usr/src/media_build_experimental/v4l/media.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/media.ko
  CC      /usr/src/media_build_experimental/v4l/meye.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/meye.ko
  CC      /usr/src/media_build_experimental/v4l/ml86v7667.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ml86v7667.ko
  CC      /usr/src/media_build_experimental/v4l/msi001.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/msi001.ko
  CC      /usr/src/media_build_experimental/v4l/msi2500.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/msi2500.ko
  CC      /usr/src/media_build_experimental/v4l/msp3400.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/msp3400.ko
  CC      /usr/src/media_build_experimental/v4l/mt2060.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt2060.ko
  CC      /usr/src/media_build_experimental/v4l/mt2063.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt2063.ko
  CC      /usr/src/media_build_experimental/v4l/mt20xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt20xx.ko
  CC      /usr/src/media_build_experimental/v4l/mt2131.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt2131.ko
  CC      /usr/src/media_build_experimental/v4l/mt2266.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt2266.ko
  CC      /usr/src/media_build_experimental/v4l/mt312.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt312.ko
  CC      /usr/src/media_build_experimental/v4l/mt352.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt352.ko
  CC      /usr/src/media_build_experimental/v4l/mt9m001.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9m001.ko
  CC      /usr/src/media_build_experimental/v4l/mt9m032.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9m032.ko
  CC      /usr/src/media_build_experimental/v4l/mt9m111.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9m111.ko
  CC      /usr/src/media_build_experimental/v4l/mt9p031.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9p031.ko
  CC      /usr/src/media_build_experimental/v4l/mt9t001.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9t001.ko
  CC      /usr/src/media_build_experimental/v4l/mt9t031.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9t031.ko
  CC      /usr/src/media_build_experimental/v4l/mt9t112.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9t112.ko
  CC      /usr/src/media_build_experimental/v4l/mt9v011.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9v011.ko
  CC      /usr/src/media_build_experimental/v4l/mt9v022.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9v022.ko
  CC      /usr/src/media_build_experimental/v4l/mt9v032.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mt9v032.ko
  CC      /usr/src/media_build_experimental/v4l/mxb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxb.ko
  CC      /usr/src/media_build_experimental/v4l/mxl111sf-demod.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxl111sf-demod.ko
  CC      /usr/src/media_build_experimental/v4l/mxl111sf-tuner.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxl111sf-tuner.ko
  CC      /usr/src/media_build_experimental/v4l/mxl301rf.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxl301rf.ko
  CC      /usr/src/media_build_experimental/v4l/mxl5005s.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxl5005s.ko
  CC      /usr/src/media_build_experimental/v4l/mxl5007t.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxl5007t.ko
  CC      /usr/src/media_build_experimental/v4l/mxl5xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/mxl5xx.ko
  CC      /usr/src/media_build_experimental/v4l/ngene.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ngene.ko
  CC      /usr/src/media_build_experimental/v4l/noon010pc30.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/noon010pc30.ko
  CC      /usr/src/media_build_experimental/v4l/nuvoton-cir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/nuvoton-cir.ko
  CC      /usr/src/media_build_experimental/v4l/nxt200x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/nxt200x.ko
  CC      /usr/src/media_build_experimental/v4l/nxt6000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/nxt6000.ko
  CC      /usr/src/media_build_experimental/v4l/or51132.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/or51132.ko
  CC      /usr/src/media_build_experimental/v4l/or51211.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/or51211.ko
  CC      /usr/src/media_build_experimental/v4l/ov2640.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov2640.ko
  CC      /usr/src/media_build_experimental/v4l/ov5642.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov5642.ko
  CC      /usr/src/media_build_experimental/v4l/ov6650.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov6650.ko
  CC      /usr/src/media_build_experimental/v4l/ov7640.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov7640.ko
  CC      /usr/src/media_build_experimental/v4l/ov7670.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov7670.ko
  CC      /usr/src/media_build_experimental/v4l/ov772x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov772x.ko
  CC      /usr/src/media_build_experimental/v4l/ov9640.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov9640.ko
  CC      /usr/src/media_build_experimental/v4l/ov9650.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov9650.ko
  CC      /usr/src/media_build_experimental/v4l/ov9740.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ov9740.ko
  CC      /usr/src/media_build_experimental/v4l/pluto2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/pluto2.ko
  CC      /usr/src/media_build_experimental/v4l/poseidon.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/poseidon.ko
  CC      /usr/src/media_build_experimental/v4l/pvrusb2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/pvrusb2.ko
  CC      /usr/src/media_build_experimental/v4l/pwc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/pwc.ko
  CC      /usr/src/media_build_experimental/v4l/qm1d1c0042.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/qm1d1c0042.ko
  CC      /usr/src/media_build_experimental/v4l/qt1010.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/qt1010.ko
  CC      /usr/src/media_build_experimental/v4l/r820t.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/r820t.ko
  CC      /usr/src/media_build_experimental/v4l/radio-bcm2048.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-bcm2048.ko
  CC      /usr/src/media_build_experimental/v4l/radio-keene.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-keene.ko
  CC      /usr/src/media_build_experimental/v4l/radio-ma901.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-ma901.ko
  CC      /usr/src/media_build_experimental/v4l/radio-maxiradio.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-maxiradio.ko
  CC      /usr/src/media_build_experimental/v4l/radio-mr800.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-mr800.ko
  CC      /usr/src/media_build_experimental/v4l/radio-platform-si4713.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-platform-si4713.ko
  CC      /usr/src/media_build_experimental/v4l/radio-raremono.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-raremono.ko
  CC      /usr/src/media_build_experimental/v4l/radio-shark.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-shark.ko
  CC      /usr/src/media_build_experimental/v4l/radio-si476x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-si476x.ko
  CC      /usr/src/media_build_experimental/v4l/radio-tea5764.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-tea5764.ko
  CC      /usr/src/media_build_experimental/v4l/radio-timb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-timb.ko
  CC      /usr/src/media_build_experimental/v4l/radio-usb-si470x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-usb-si470x.ko
  CC      /usr/src/media_build_experimental/v4l/radio-usb-si4713.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-usb-si4713.ko
  CC      /usr/src/media_build_experimental/v4l/radio-wl1273.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/radio-wl1273.ko
  CC      /usr/src/media_build_experimental/v4l/rc-adstech-dvb-t-pci.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-adstech-dvb-t-pci.ko
  CC      /usr/src/media_build_experimental/v4l/rc-alink-dtu-m.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-alink-dtu-m.ko
  CC      /usr/src/media_build_experimental/v4l/rc-anysee.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-anysee.ko
  CC      /usr/src/media_build_experimental/v4l/rc-apac-viewcomp.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-apac-viewcomp.ko
  CC      /usr/src/media_build_experimental/v4l/rc-asus-pc39.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-asus-pc39.ko
  CC      /usr/src/media_build_experimental/v4l/rc-asus-ps3-100.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-asus-ps3-100.ko
  CC      /usr/src/media_build_experimental/v4l/rc-ati-tv-wonder-hd-600.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-ati-tv-wonder-hd-600.ko
  CC      /usr/src/media_build_experimental/v4l/rc-ati-x10.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-ati-x10.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia-a16d.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-a16d.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia-cardbus.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-cardbus.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia-dvbt.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-dvbt.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia-m135a.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-m135a.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia-m733a-rm-k6.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-m733a-rm-k6.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia-rm-ks.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia-rm-ks.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avermedia.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avermedia.ko
  CC      /usr/src/media_build_experimental/v4l/rc-avertv-303.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-avertv-303.ko
  CC      /usr/src/media_build_experimental/v4l/rc-azurewave-ad-tu700.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-azurewave-ad-tu700.ko
  CC      /usr/src/media_build_experimental/v4l/rc-behold-columbus.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-behold-columbus.ko
  CC      /usr/src/media_build_experimental/v4l/rc-behold.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-behold.ko
  CC      /usr/src/media_build_experimental/v4l/rc-budget-ci-old.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-budget-ci-old.ko
  CC      /usr/src/media_build_experimental/v4l/rc-cinergy-1400.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-cinergy-1400.ko
  CC      /usr/src/media_build_experimental/v4l/rc-cinergy.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-cinergy.ko
  CC      /usr/src/media_build_experimental/v4l/rc-core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-core.ko
  CC      /usr/src/media_build_experimental/v4l/rc-delock-61959.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-delock-61959.ko
  CC      /usr/src/media_build_experimental/v4l/rc-dib0700-nec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-dib0700-nec.ko
  CC      /usr/src/media_build_experimental/v4l/rc-dib0700-rc5.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-dib0700-rc5.ko
  CC      /usr/src/media_build_experimental/v4l/rc-digitalnow-tinytwin.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-digitalnow-tinytwin.ko
  CC      /usr/src/media_build_experimental/v4l/rc-digittrade.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-digittrade.ko
  CC      /usr/src/media_build_experimental/v4l/rc-dm1105-nec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-dm1105-nec.ko
  CC      /usr/src/media_build_experimental/v4l/rc-dntv-live-dvb-t.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-dntv-live-dvb-t.ko
  CC      /usr/src/media_build_experimental/v4l/rc-dntv-live-dvbt-pro.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-dntv-live-dvbt-pro.ko
  CC      /usr/src/media_build_experimental/v4l/rc-dvbsky.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-dvbsky.ko
  CC      /usr/src/media_build_experimental/v4l/rc-em-terratec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-em-terratec.ko
  CC      /usr/src/media_build_experimental/v4l/rc-encore-enltv-fm53.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-encore-enltv-fm53.ko
  CC      /usr/src/media_build_experimental/v4l/rc-encore-enltv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-encore-enltv.ko
  CC      /usr/src/media_build_experimental/v4l/rc-encore-enltv2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-encore-enltv2.ko
  CC      /usr/src/media_build_experimental/v4l/rc-evga-indtube.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-evga-indtube.ko
  CC      /usr/src/media_build_experimental/v4l/rc-eztv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-eztv.ko
  CC      /usr/src/media_build_experimental/v4l/rc-flydvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-flydvb.ko
  CC      /usr/src/media_build_experimental/v4l/rc-flyvideo.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-flyvideo.ko
  CC      /usr/src/media_build_experimental/v4l/rc-fusionhdtv-mce.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-fusionhdtv-mce.ko
  CC      /usr/src/media_build_experimental/v4l/rc-gadmei-rm008z.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-gadmei-rm008z.ko
  CC      /usr/src/media_build_experimental/v4l/rc-genius-tvgo-a11mce.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-genius-tvgo-a11mce.ko
  CC      /usr/src/media_build_experimental/v4l/rc-gotview7135.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-gotview7135.ko
  CC      /usr/src/media_build_experimental/v4l/rc-hauppauge.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-hauppauge.ko
  CC      /usr/src/media_build_experimental/v4l/rc-imon-mce.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-imon-mce.ko
  CC      /usr/src/media_build_experimental/v4l/rc-imon-pad.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-imon-pad.ko
  CC      /usr/src/media_build_experimental/v4l/rc-iodata-bctv7e.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-iodata-bctv7e.ko
  CC      /usr/src/media_build_experimental/v4l/rc-it913x-v1.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-it913x-v1.ko
  CC      /usr/src/media_build_experimental/v4l/rc-it913x-v2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-it913x-v2.ko
  CC      /usr/src/media_build_experimental/v4l/rc-kaiomy.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-kaiomy.ko
  CC      /usr/src/media_build_experimental/v4l/rc-kworld-315u.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-kworld-315u.ko
  CC      /usr/src/media_build_experimental/v4l/rc-kworld-pc150u.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-kworld-pc150u.ko
  CC      /usr/src/media_build_experimental/v4l/rc-kworld-plus-tv-analog.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-kworld-plus-tv-analog.ko
  CC      /usr/src/media_build_experimental/v4l/rc-leadtek-y04g0051.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-leadtek-y04g0051.ko
  CC      /usr/src/media_build_experimental/v4l/rc-lirc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-lirc.ko
  CC      /usr/src/media_build_experimental/v4l/rc-lme2510.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-lme2510.ko
  CC      /usr/src/media_build_experimental/v4l/rc-loopback.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-loopback.ko
  CC      /usr/src/media_build_experimental/v4l/rc-manli.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-manli.ko
  CC      /usr/src/media_build_experimental/v4l/rc-medion-x10-digitainer.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-medion-x10-digitainer.ko
  CC      /usr/src/media_build_experimental/v4l/rc-medion-x10-or2x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-medion-x10-or2x.ko
  CC      /usr/src/media_build_experimental/v4l/rc-medion-x10.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-medion-x10.ko
  CC      /usr/src/media_build_experimental/v4l/rc-msi-digivox-ii.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-msi-digivox-ii.ko
  CC      /usr/src/media_build_experimental/v4l/rc-msi-digivox-iii.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-msi-digivox-iii.ko
  CC      /usr/src/media_build_experimental/v4l/rc-msi-tvanywhere-plus.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-msi-tvanywhere-plus.ko
  CC      /usr/src/media_build_experimental/v4l/rc-msi-tvanywhere.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-msi-tvanywhere.ko
  CC      /usr/src/media_build_experimental/v4l/rc-nebula.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-nebula.ko
  CC      /usr/src/media_build_experimental/v4l/rc-nec-terratec-cinergy-xs.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-nec-terratec-cinergy-xs.ko
  CC      /usr/src/media_build_experimental/v4l/rc-norwood.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-norwood.ko
  CC      /usr/src/media_build_experimental/v4l/rc-npgtech.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-npgtech.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pctv-sedna.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pctv-sedna.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pinnacle-color.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pinnacle-color.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pinnacle-grey.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pinnacle-grey.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pinnacle-pctv-hd.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pinnacle-pctv-hd.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pixelview-002t.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pixelview-002t.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pixelview-mk12.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pixelview-mk12.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pixelview-new.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pixelview-new.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pixelview.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pixelview.ko
  CC      /usr/src/media_build_experimental/v4l/rc-powercolor-real-angel.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-powercolor-real-angel.ko
  CC      /usr/src/media_build_experimental/v4l/rc-proteus-2309.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-proteus-2309.ko
  CC      /usr/src/media_build_experimental/v4l/rc-purpletv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-purpletv.ko
  CC      /usr/src/media_build_experimental/v4l/rc-pv951.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-pv951.ko
  CC      /usr/src/media_build_experimental/v4l/rc-rc6-mce.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-rc6-mce.ko
  CC      /usr/src/media_build_experimental/v4l/rc-real-audio-220-32-keys.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-real-audio-220-32-keys.ko
  CC      /usr/src/media_build_experimental/v4l/rc-reddo.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-reddo.ko
  CC      /usr/src/media_build_experimental/v4l/rc-snapstream-firefly.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-snapstream-firefly.ko
  CC      /usr/src/media_build_experimental/v4l/rc-streamzap.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-streamzap.ko
  CC      /usr/src/media_build_experimental/v4l/rc-su3000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-su3000.ko
  CC      /usr/src/media_build_experimental/v4l/rc-tbs-nec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-tbs-nec.ko
  CC      /usr/src/media_build_experimental/v4l/rc-technisat-usb2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-technisat-usb2.ko
  CC      /usr/src/media_build_experimental/v4l/rc-terratec-cinergy-xs.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-terratec-cinergy-xs.ko
  CC      /usr/src/media_build_experimental/v4l/rc-terratec-slim-2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-terratec-slim-2.ko
  CC      /usr/src/media_build_experimental/v4l/rc-terratec-slim.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-terratec-slim.ko
  CC      /usr/src/media_build_experimental/v4l/rc-tevii-nec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-tevii-nec.ko
  CC      /usr/src/media_build_experimental/v4l/rc-tivo.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-tivo.ko
  CC      /usr/src/media_build_experimental/v4l/rc-total-media-in-hand-02.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-total-media-in-hand-02.ko
  CC      /usr/src/media_build_experimental/v4l/rc-total-media-in-hand.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-total-media-in-hand.ko
  CC      /usr/src/media_build_experimental/v4l/rc-trekstor.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-trekstor.ko
  CC      /usr/src/media_build_experimental/v4l/rc-tt-1500.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-tt-1500.ko
  CC      /usr/src/media_build_experimental/v4l/rc-twinhan1027.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-twinhan1027.ko
  CC      /usr/src/media_build_experimental/v4l/rc-videomate-m1f.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-videomate-m1f.ko
  CC      /usr/src/media_build_experimental/v4l/rc-videomate-s350.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-videomate-s350.ko
  CC      /usr/src/media_build_experimental/v4l/rc-videomate-tv-pvr.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-videomate-tv-pvr.ko
  CC      /usr/src/media_build_experimental/v4l/rc-winfast-usbii-deluxe.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-winfast-usbii-deluxe.ko
  CC      /usr/src/media_build_experimental/v4l/rc-winfast.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rc-winfast.ko
  CC      /usr/src/media_build_experimental/v4l/redrat3.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/redrat3.ko
  CC      /usr/src/media_build_experimental/v4l/rj54n1cb0c.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rj54n1cb0c.ko
  CC      /usr/src/media_build_experimental/v4l/rtl2830.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rtl2830.ko
  CC      /usr/src/media_build_experimental/v4l/rtl2832.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rtl2832.ko
  CC      /usr/src/media_build_experimental/v4l/rtl2832_sdr.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/rtl2832_sdr.ko
  CC      /usr/src/media_build_experimental/v4l/s2250.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s2250.ko
  CC      /usr/src/media_build_experimental/v4l/s2255drv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s2255drv.ko
  CC      /usr/src/media_build_experimental/v4l/s5c73m3.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5c73m3.ko
  CC      /usr/src/media_build_experimental/v4l/s5h1409.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5h1409.ko
  CC      /usr/src/media_build_experimental/v4l/s5h1411.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5h1411.ko
  CC      /usr/src/media_build_experimental/v4l/s5h1420.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5h1420.ko
  CC      /usr/src/media_build_experimental/v4l/s5h1432.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5h1432.ko
  CC      /usr/src/media_build_experimental/v4l/s5k4ecgx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5k4ecgx.ko
  CC      /usr/src/media_build_experimental/v4l/s5k5baf.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5k5baf.ko
  CC      /usr/src/media_build_experimental/v4l/s5k6a3.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5k6a3.ko
  CC      /usr/src/media_build_experimental/v4l/s5k6aa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s5k6aa.ko
  CC      /usr/src/media_build_experimental/v4l/s921.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/s921.ko
  CC      /usr/src/media_build_experimental/v4l/saa6588.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa6588.ko
  CC      /usr/src/media_build_experimental/v4l/saa6752hs.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa6752hs.ko
  CC      /usr/src/media_build_experimental/v4l/saa7110.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7110.ko
  CC      /usr/src/media_build_experimental/v4l/saa7115.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7115.ko
  CC      /usr/src/media_build_experimental/v4l/saa7127.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7127.ko
  CC      /usr/src/media_build_experimental/v4l/saa7134-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7134-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/saa7134-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7134-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/saa7134-empress.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7134-empress.ko
  CC      /usr/src/media_build_experimental/v4l/saa7134-go7007.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7134-go7007.ko
  CC      /usr/src/media_build_experimental/v4l/saa7134.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7134.ko
  CC      /usr/src/media_build_experimental/v4l/saa7146.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7146.ko
  CC      /usr/src/media_build_experimental/v4l/saa7146_vv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7146_vv.ko
  CC      /usr/src/media_build_experimental/v4l/saa7164.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7164.ko
  CC      /usr/src/media_build_experimental/v4l/saa716x_budget.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa716x_budget.ko
  CC      /usr/src/media_build_experimental/v4l/saa716x_core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa716x_core.ko
  CC      /usr/src/media_build_experimental/v4l/saa716x_ff.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa716x_ff.ko
  CC      /usr/src/media_build_experimental/v4l/saa716x_hybrid.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa716x_hybrid.ko
  CC      /usr/src/media_build_experimental/v4l/saa717x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa717x.ko
  CC      /usr/src/media_build_experimental/v4l/saa7185.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7185.ko
  CC      /usr/src/media_build_experimental/v4l/saa7191.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7191.ko
  CC      /usr/src/media_build_experimental/v4l/saa7706h.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/saa7706h.ko
  CC      /usr/src/media_build_experimental/v4l/sh_veu.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/sh_veu.ko
  CC      /usr/src/media_build_experimental/v4l/shark2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/shark2.ko
  CC      /usr/src/media_build_experimental/v4l/si2157.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/si2157.ko
  CC      /usr/src/media_build_experimental/v4l/si2165.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/si2165.ko
  CC      /usr/src/media_build_experimental/v4l/si2168.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/si2168.ko
  CC      /usr/src/media_build_experimental/v4l/si21xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/si21xx.ko
  CC      /usr/src/media_build_experimental/v4l/si4713.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/si4713.ko
  CC      /usr/src/media_build_experimental/v4l/smiapp-pll.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smiapp-pll.ko
  CC      /usr/src/media_build_experimental/v4l/smiapp.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smiapp.ko
  CC      /usr/src/media_build_experimental/v4l/smipcie.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smipcie.ko
  CC      /usr/src/media_build_experimental/v4l/smsdvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smsdvb.ko
  CC      /usr/src/media_build_experimental/v4l/smsmdtv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smsmdtv.ko
  CC      /usr/src/media_build_experimental/v4l/smssdio.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smssdio.ko
  CC      /usr/src/media_build_experimental/v4l/smsusb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/smsusb.ko
  CC      /usr/src/media_build_experimental/v4l/snd-bt87x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/snd-bt87x.ko
  CC      /usr/src/media_build_experimental/v4l/soc_camera.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/soc_camera.ko
  CC      /usr/src/media_build_experimental/v4l/soc_camera_platform.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/soc_camera_platform.ko
  CC      /usr/src/media_build_experimental/v4l/soc_mediabus.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/soc_mediabus.ko
  CC      /usr/src/media_build_experimental/v4l/soc_scale_crop.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/soc_scale_crop.ko
  CC      /usr/src/media_build_experimental/v4l/solo6x10.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/solo6x10.ko
  CC      /usr/src/media_build_experimental/v4l/sony-btf-mpx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/sony-btf-mpx.ko
  CC      /usr/src/media_build_experimental/v4l/sp2.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/sp2.ko
  CC      /usr/src/media_build_experimental/v4l/sp8870.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/sp8870.ko
  CC      /usr/src/media_build_experimental/v4l/sp887x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/sp887x.ko
  CC      /usr/src/media_build_experimental/v4l/sr030pc30.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/sr030pc30.ko
  CC      /usr/src/media_build_experimental/v4l/stb0899.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stb0899.ko
  CC      /usr/src/media_build_experimental/v4l/stb6000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stb6000.ko
  CC      /usr/src/media_build_experimental/v4l/stb6100.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stb6100.ko
  CC      /usr/src/media_build_experimental/v4l/stk1160.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stk1160.ko
  CC      /usr/src/media_build_experimental/v4l/stkwebcam.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stkwebcam.ko
  CC      /usr/src/media_build_experimental/v4l/streamzap.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/streamzap.ko
  CC      /usr/src/media_build_experimental/v4l/stv0288.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0288.ko
  CC      /usr/src/media_build_experimental/v4l/stv0297.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0297.ko
  CC      /usr/src/media_build_experimental/v4l/stv0299.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0299.ko
  CC      /usr/src/media_build_experimental/v4l/stv0367.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0367.ko
  CC      /usr/src/media_build_experimental/v4l/stv0367dd.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0367dd.ko
  CC      /usr/src/media_build_experimental/v4l/stv0900.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0900.ko
  CC      /usr/src/media_build_experimental/v4l/stv090x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv090x.ko
  CC      /usr/src/media_build_experimental/v4l/stv0910.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv0910.ko
  CC      /usr/src/media_build_experimental/v4l/stv6110.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv6110.ko
  CC      /usr/src/media_build_experimental/v4l/stv6110x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv6110x.ko
  CC      /usr/src/media_build_experimental/v4l/stv6111.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/stv6111.ko
  CC      /usr/src/media_build_experimental/v4l/tc90522.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tc90522.ko
  CC      /usr/src/media_build_experimental/v4l/tcm825x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tcm825x.ko
  CC      /usr/src/media_build_experimental/v4l/tda10021.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda10021.ko
  CC      /usr/src/media_build_experimental/v4l/tda10023.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda10023.ko
  CC      /usr/src/media_build_experimental/v4l/tda10048.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda10048.ko
  CC      /usr/src/media_build_experimental/v4l/tda1004x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda1004x.ko
  CC      /usr/src/media_build_experimental/v4l/tda10071.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda10071.ko
  CC      /usr/src/media_build_experimental/v4l/tda10086.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda10086.ko
  CC      /usr/src/media_build_experimental/v4l/tda18212.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda18212.ko
  CC      /usr/src/media_build_experimental/v4l/tda18212dd.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda18212dd.ko
  CC      /usr/src/media_build_experimental/v4l/tda18218.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda18218.ko
  CC      /usr/src/media_build_experimental/v4l/tda18271.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda18271.ko
  CC      /usr/src/media_build_experimental/v4l/tda18271c2dd.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda18271c2dd.ko
  CC      /usr/src/media_build_experimental/v4l/tda665x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda665x.ko
  CC      /usr/src/media_build_experimental/v4l/tda7432.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda7432.ko
  CC      /usr/src/media_build_experimental/v4l/tda8083.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda8083.ko
  CC      /usr/src/media_build_experimental/v4l/tda8261.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda8261.ko
  CC      /usr/src/media_build_experimental/v4l/tda826x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda826x.ko
  CC      /usr/src/media_build_experimental/v4l/tda827x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda827x.ko
  CC      /usr/src/media_build_experimental/v4l/tda8290.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda8290.ko
  CC      /usr/src/media_build_experimental/v4l/tda9840.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda9840.ko
  CC      /usr/src/media_build_experimental/v4l/tda9887.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tda9887.ko
  CC      /usr/src/media_build_experimental/v4l/tea575x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tea575x.ko
  CC      /usr/src/media_build_experimental/v4l/tea5761.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tea5761.ko
  CC      /usr/src/media_build_experimental/v4l/tea5767.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tea5767.ko
  CC      /usr/src/media_build_experimental/v4l/tea6415c.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tea6415c.ko
  CC      /usr/src/media_build_experimental/v4l/tea6420.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tea6420.ko
  CC      /usr/src/media_build_experimental/v4l/tef6862.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tef6862.ko
  CC      /usr/src/media_build_experimental/v4l/ths7303.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ths7303.ko
  CC      /usr/src/media_build_experimental/v4l/ths8200.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ths8200.ko
  CC      /usr/src/media_build_experimental/v4l/timblogiw.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/timblogiw.ko
  CC      /usr/src/media_build_experimental/v4l/tlv320aic23b.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tlv320aic23b.ko
  CC      /usr/src/media_build_experimental/v4l/tm6000-alsa.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tm6000-alsa.ko
  CC      /usr/src/media_build_experimental/v4l/tm6000-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tm6000-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/tm6000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tm6000.ko
  CC      /usr/src/media_build_experimental/v4l/ts2020.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ts2020.ko
  CC      /usr/src/media_build_experimental/v4l/ttpci-eeprom.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ttpci-eeprom.ko
  CC      /usr/src/media_build_experimental/v4l/ttusb_dec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ttusb_dec.ko
  CC      /usr/src/media_build_experimental/v4l/ttusbdecfe.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ttusbdecfe.ko
  CC      /usr/src/media_build_experimental/v4l/ttusbir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ttusbir.ko
  CC      /usr/src/media_build_experimental/v4l/tua6100.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tua6100.ko
  CC      /usr/src/media_build_experimental/v4l/tua9001.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tua9001.ko
  CC      /usr/src/media_build_experimental/v4l/tuner-simple.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tuner-simple.ko
  CC      /usr/src/media_build_experimental/v4l/tuner-types.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tuner-types.ko
  CC      /usr/src/media_build_experimental/v4l/tuner-xc2028.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tuner-xc2028.ko
  CC      /usr/src/media_build_experimental/v4l/tuner.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tuner.ko
  CC      /usr/src/media_build_experimental/v4l/tvaudio.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tvaudio.ko
  CC      /usr/src/media_build_experimental/v4l/tveeprom.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tveeprom.ko
  CC      /usr/src/media_build_experimental/v4l/tvp514x.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tvp514x.ko
  CC      /usr/src/media_build_experimental/v4l/tvp5150.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tvp5150.ko
  CC      /usr/src/media_build_experimental/v4l/tvp7002.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tvp7002.ko
  CC      /usr/src/media_build_experimental/v4l/tw2804.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tw2804.ko
  CC      /usr/src/media_build_experimental/v4l/tw68.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tw68.ko
  CC      /usr/src/media_build_experimental/v4l/tw9903.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tw9903.ko
  CC      /usr/src/media_build_experimental/v4l/tw9906.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tw9906.ko
  CC      /usr/src/media_build_experimental/v4l/tw9910.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/tw9910.ko
  CC      /usr/src/media_build_experimental/v4l/uda1342.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/uda1342.ko
  CC      /usr/src/media_build_experimental/v4l/upd64031a.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/upd64031a.ko
  CC      /usr/src/media_build_experimental/v4l/upd64083.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/upd64083.ko
  CC      /usr/src/media_build_experimental/v4l/usbtv.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/usbtv.ko
  CC      /usr/src/media_build_experimental/v4l/usbvision.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/usbvision.ko
  CC      /usr/src/media_build_experimental/v4l/uvcvideo.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/uvcvideo.ko
  CC      /usr/src/media_build_experimental/v4l/v4l2-common.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/v4l2-common.ko
  CC      /usr/src/media_build_experimental/v4l/v4l2-dv-timings.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/v4l2-dv-timings.ko
  CC      /usr/src/media_build_experimental/v4l/v4l2-int-device.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/v4l2-int-device.ko
  CC      /usr/src/media_build_experimental/v4l/v4l2-mem2mem.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/v4l2-mem2mem.ko
  CC      /usr/src/media_build_experimental/v4l/ves1820.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ves1820.ko
  CC      /usr/src/media_build_experimental/v4l/ves1x93.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/ves1x93.ko
  CC      /usr/src/media_build_experimental/v4l/via-camera.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/via-camera.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf-core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf-core.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf-dma-contig.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf-dma-contig.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf-dma-sg.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf-dma-sg.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf-vmalloc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf-vmalloc.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf2-core.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf2-core.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf2-dma-contig.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf2-dma-contig.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf2-dma-sg.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf2-dma-sg.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf2-dvb.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf2-dvb.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf2-memops.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf2-memops.ko
  CC      /usr/src/media_build_experimental/v4l/videobuf2-vmalloc.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videobuf2-vmalloc.ko
  CC      /usr/src/media_build_experimental/v4l/videocodec.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videocodec.ko
  CC      /usr/src/media_build_experimental/v4l/videodev.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/videodev.ko
  CC      /usr/src/media_build_experimental/v4l/vim2m.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/vim2m.ko
  CC      /usr/src/media_build_experimental/v4l/vivid.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/vivid.ko
  CC      /usr/src/media_build_experimental/v4l/vp27smpx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/vp27smpx.ko
  CC      /usr/src/media_build_experimental/v4l/vpx3220.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/vpx3220.ko
  CC      /usr/src/media_build_experimental/v4l/vs6624.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/vs6624.ko
  CC      /usr/src/media_build_experimental/v4l/w9966.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/w9966.ko
  CC      /usr/src/media_build_experimental/v4l/winbond-cir.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/winbond-cir.ko
  CC      /usr/src/media_build_experimental/v4l/wm8739.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/wm8739.ko
  CC      /usr/src/media_build_experimental/v4l/wm8775.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/wm8775.ko
  CC      /usr/src/media_build_experimental/v4l/xc4000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/xc4000.ko
  CC      /usr/src/media_build_experimental/v4l/xc5000.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/xc5000.ko
  CC      /usr/src/media_build_experimental/v4l/zl10036.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zl10036.ko
  CC      /usr/src/media_build_experimental/v4l/zl10039.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zl10039.ko
  CC      /usr/src/media_build_experimental/v4l/zl10353.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zl10353.ko
  CC      /usr/src/media_build_experimental/v4l/zr36016.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zr36016.ko
  CC      /usr/src/media_build_experimental/v4l/zr36050.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zr36050.ko
  CC      /usr/src/media_build_experimental/v4l/zr36060.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zr36060.ko
  CC      /usr/src/media_build_experimental/v4l/zr36067.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zr36067.ko
  CC      /usr/src/media_build_experimental/v4l/zr364xx.mod.o
  LD [M]  /usr/src/media_build_experimental/v4l/zr364xx.ko
make[2]: Leaving directory '/usr/src/linux-headers-3.16.0-30-generic'
./scripts/rmmod.pl check
found 630 modules
make[1]: Leaving directory '/usr/src/media_build_experimental/v4l'
make -C /usr/src/media_build_experimental/v4l install
make[1]: Entering directory '/usr/src/media_build_experimental/v4l'
removed '/lib/modules/3.16.0-30-generic/updates/media/snd-bt87x.ko'
removed directory: '/lib/modules/3.16.0-30-generic/updates/media'
/sbin/depmod -a 3.16.0-30-generic 
make -C firmware install
make[2]: Entering directory '/usr/src/media_build_experimental/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory '/usr/src/media_build_experimental/v4l/firmware'
install -d -v /lib/modules/3.16.0-30-generic/updates/media
install: creating directory '/lib/modules/3.16.0-30-generic/updates/media'
install a8293.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ad9389b.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adp1653.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7170.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7175.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7180.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7183.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7343.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7393.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7511.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7604.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install adv7842.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install af9013.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install af9033.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install airspy.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ak881x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install altera-ci.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install altera-stapl.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install aptina-pll.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install as102_fe.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install as3645a.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install atbm8830.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ati_remote.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install au0828.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install au8522_common.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install au8522_decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install au8522_dig.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install b2c2-flexcop-pci.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install b2c2-flexcop-usb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install b2c2-flexcop.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bcm3510.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bt819.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bt856.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bt866.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bt878.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install btcx-risc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bttv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install budget-av.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install budget-ci.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install budget-core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install budget-patch.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install budget.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install bw-qcam.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install c-qcam.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cafe_ccic.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cpia2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cs5345.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cs53l32a.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx18-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx18.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx22700.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx22702.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx231xx-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx231xx-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx231xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx2341x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx23885.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx24110.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx24113.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx24116.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx24117.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx24123.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx25821-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx25821.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx25840.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx88-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx88-blackbird.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx88-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx88-vp3054-i2c.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx8800.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx8802.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cx88xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cxd2099.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cxd2820r.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cxd2843.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install cypress_firmware.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ddbridge.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib0070.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib0090.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib3000mb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib3000mc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib7000m.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib7000p.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib8000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dib9000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dibx000_common.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dm1105.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install drx39xyj.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install drxd.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install drxk.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ds3000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dsbr100.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dst.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dst_ca.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dt3155v4l.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-as102.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-bt8xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-pll.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-ttpci.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-ttusb-budget.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-a800.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-af9005-remote.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-af9005.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-af9015.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-af9035.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-anysee.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-au6610.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-az6007.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-az6027.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-ce6230.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-cinergyT2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-cxusb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dib0700.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dibusb-common.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dibusb-mb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dibusb-mc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-digitv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dtt200u.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dtv5100.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dvbsky.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-dw2102.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-ec168.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-friio.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-gl861.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-gp8psk.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-lmedm04.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-m920x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-mxl111sf.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-nova-t-usb2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-opera.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-pctv452e.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-rtl28xxu.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-technisat-usb2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-ttusb2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-umt-010.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-vp702x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb-vp7045.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb-usb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb_dummy_fe.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install dvb_usb_v2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install e4000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install earth-pt1.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install earth-pt3.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ec100.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install em28xx-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install em28xx-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install em28xx-rc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install em28xx-v4l.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install em28xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ene_ir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install fc0011.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install fc0012.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install fc0013.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install fc2580.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install fintek-cir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install firedtv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install fm_drv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install go7007-loader.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install go7007-usb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install go7007.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gpio-ir-recv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_benq.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_conex.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_cpia1.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_dtcs033.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_etoms.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_finepix.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_gl860.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_jeilinj.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_jl2005bcd.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_kinect.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_konica.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_m5602.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_main.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_mars.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_mr97310a.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_nw80x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_ov519.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_ov534.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_ov534_9.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_pac207.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_pac7302.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_pac7311.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_se401.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sn9c2028.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sn9c20x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sonixb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sonixj.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca1528.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca500.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca501.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca505.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca506.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca508.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_spca561.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sq905.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sq905c.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sq930x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_stk014.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_stk1135.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_stv0680.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_stv06xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_sunplus.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_t613.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_topro.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_tv8532.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_vc032x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_vicam.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_xirlink_cit.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install gspca_zc3xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install hackrf.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install hd29l2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install hdpvr.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install hexium_gemini.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install hexium_orion.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install hopper.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install igorplugusb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install iguanair.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install img-ir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install imon.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install imx074.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-hix5hd2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-jvc-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-kbd-i2c.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-lirc-codec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-mce_kbd-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-nec-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-rc5-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-rc6-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-sanyo-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-sharp-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-sony-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ir-xmp-decoder.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install isl6405.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install isl6421.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install isl6423.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install it913x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install itd1000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ite-cir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ivtv-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ivtv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ivtvfb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ix2505v.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ks0127.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install l64781.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lg2160.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lgdt3305.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lgdt330x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lgs8gl5.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lgs8gxx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_bt829.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_dev.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_imon.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_parallel.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_sasem.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_serial.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_sir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lirc_zilog.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lm3560.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lm3646.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lnbp21.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install lnbp22.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m2m-deinterlace.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m52790.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m5mols.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m88ds3103.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m88rs2000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m88rs6000t.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install m88ts2022.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mantis.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mantis_core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install max2165.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mb86a16.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mb86a20s.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mc44s803.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mceusb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install media.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install meye.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ml86v7667.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install msi001.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install msi2500.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install msp3400.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt2060.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt2063.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt20xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt2131.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt2266.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt312.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt352.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9m001.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9m032.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9m111.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9p031.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9t001.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9t031.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9t112.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9v011.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9v022.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mt9v032.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxl111sf-demod.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxl111sf-tuner.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxl301rf.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxl5005s.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxl5007t.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install mxl5xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ngene.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install noon010pc30.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install nuvoton-cir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install nxt200x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install nxt6000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install or51132.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install or51211.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov2640.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov5642.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov6650.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov7640.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov7670.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov772x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov9640.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov9650.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ov9740.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install pluto2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install poseidon.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install pvrusb2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install pwc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install qm1d1c0042.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install qt1010.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install r820t.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-bcm2048.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-keene.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-ma901.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-maxiradio.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-mr800.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-platform-si4713.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-raremono.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-shark.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-si476x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-tea5764.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-timb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-usb-si470x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-usb-si4713.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install radio-wl1273.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-adstech-dvb-t-pci.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-alink-dtu-m.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-anysee.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-apac-viewcomp.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-asus-pc39.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-asus-ps3-100.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-ati-tv-wonder-hd-600.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-ati-x10.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia-a16d.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia-cardbus.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia-dvbt.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia-m135a.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia-m733a-rm-k6.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia-rm-ks.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avermedia.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-avertv-303.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-azurewave-ad-tu700.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-behold-columbus.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-behold.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-budget-ci-old.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-cinergy-1400.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-cinergy.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-delock-61959.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-dib0700-nec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-dib0700-rc5.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-digitalnow-tinytwin.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-digittrade.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-dm1105-nec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-dntv-live-dvb-t.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-dntv-live-dvbt-pro.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-dvbsky.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-em-terratec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-encore-enltv-fm53.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-encore-enltv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-encore-enltv2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-evga-indtube.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-eztv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-flydvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-flyvideo.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-fusionhdtv-mce.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-gadmei-rm008z.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-genius-tvgo-a11mce.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-gotview7135.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-hauppauge.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-imon-mce.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-imon-pad.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-iodata-bctv7e.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-it913x-v1.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-it913x-v2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-kaiomy.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-kworld-315u.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-kworld-pc150u.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-kworld-plus-tv-analog.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-leadtek-y04g0051.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-lirc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-lme2510.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-loopback.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-manli.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-medion-x10-digitainer.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-medion-x10-or2x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-medion-x10.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-msi-digivox-ii.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-msi-digivox-iii.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-msi-tvanywhere-plus.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-msi-tvanywhere.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-nebula.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-nec-terratec-cinergy-xs.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-norwood.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-npgtech.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pctv-sedna.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pinnacle-color.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pinnacle-grey.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pinnacle-pctv-hd.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pixelview-002t.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pixelview-mk12.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pixelview-new.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pixelview.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-powercolor-real-angel.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-proteus-2309.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-purpletv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-pv951.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-rc6-mce.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-real-audio-220-32-keys.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-reddo.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-snapstream-firefly.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-streamzap.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-su3000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-tbs-nec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-technisat-usb2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-terratec-cinergy-xs.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-terratec-slim-2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-terratec-slim.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-tevii-nec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-tivo.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-total-media-in-hand-02.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-total-media-in-hand.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-trekstor.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-tt-1500.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-twinhan1027.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-videomate-m1f.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-videomate-s350.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-videomate-tv-pvr.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-winfast-usbii-deluxe.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rc-winfast.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install redrat3.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rj54n1cb0c.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rtl2830.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rtl2832.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install rtl2832_sdr.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s2250.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s2255drv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5c73m3.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5h1409.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5h1411.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5h1420.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5h1432.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5k4ecgx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5k5baf.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5k6a3.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s5k6aa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install s921.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa6588.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa6752hs.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7110.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7115.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7127.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7134-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7134-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7134-empress.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7134-go7007.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7134.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7146.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7146_vv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7164.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa716x_budget.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa716x_core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa716x_ff.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa716x_hybrid.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa717x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7185.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7191.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install saa7706h.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install sh_veu.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install shark2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install si2157.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install si2165.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install si2168.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install si21xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install si4713.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smiapp-pll.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smiapp.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smipcie.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smsdvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smsmdtv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smssdio.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install smsusb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install snd-bt87x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install soc_camera.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install soc_camera_platform.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install soc_mediabus.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install soc_scale_crop.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install solo6x10.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install sony-btf-mpx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install sp2.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install sp8870.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install sp887x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install sr030pc30.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stb0899.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stb6000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stb6100.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stk1160.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stkwebcam.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install streamzap.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0288.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0297.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0299.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0367.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0367dd.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0900.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv090x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv0910.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv6110.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv6110x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install stv6111.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tc90522.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tcm825x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda10021.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda10023.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda10048.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda1004x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda10071.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda10086.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda18212.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda18212dd.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda18218.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda18271.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda18271c2dd.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda665x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda7432.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda8083.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda8261.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda826x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda827x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda8290.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda9840.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tda9887.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tea575x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tea5761.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tea5767.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tea6415c.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tea6420.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tef6862.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ths7303.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ths8200.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install timblogiw.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tlv320aic23b.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tm6000-alsa.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tm6000-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tm6000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ts2020.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ttpci-eeprom.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ttusb_dec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ttusbdecfe.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ttusbir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tua6100.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tua9001.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tuner-simple.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tuner-types.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tuner-xc2028.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tuner.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tvaudio.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tveeprom.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tvp514x.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tvp5150.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tvp7002.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tw2804.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tw68.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tw9903.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tw9906.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install tw9910.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install uda1342.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install upd64031a.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install upd64083.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install usbtv.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install usbvision.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install uvcvideo.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install v4l2-common.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install v4l2-dv-timings.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install v4l2-int-device.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install v4l2-mem2mem.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ves1820.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install ves1x93.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install via-camera.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf-core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf-dma-contig.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf-dma-sg.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf-vmalloc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf2-core.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf2-dma-contig.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf2-dma-sg.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf2-dvb.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf2-memops.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videobuf2-vmalloc.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videocodec.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install videodev.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install vim2m.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install vivid.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install vp27smpx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install vpx3220.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install vs6624.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install w9966.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install winbond-cir.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install wm8739.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install wm8775.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install xc4000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install xc5000.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zl10036.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zl10039.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zl10353.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zr36016.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zr36050.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zr36060.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zr36067.ko -> /lib/modules/3.16.0-30-generic/updates/media/
install zr364xx.ko -> /lib/modules/3.16.0-30-generic/updates/media/
strip --strip-debug /lib/modules/3.16.0-30-generic/updates/media/*.ko
/sbin/depmod -a 3.16.0-30-generic 
make[1]: Leaving directory '/usr/src/media_build_experimental/v4l'
user@ubuntu:/usr/src/media_build_experimental$ 



```

Any help will be much appreciated.

---

### Post by Yellow Pasque on 2015-02-15
The log you provided looks like a successful build to me. Can you give more detail on what goes wrong?

---

### Post by tzorge on 2015-02-17
Well, after the built, lsmod shows the dbbridge loaded, but the hardware is not listed in TVheadend. 

Also the dmesg has this  [COLOR=#000000][FONT=Ubuntu Mono] Do not return on command ready timeout [/FONT][/COLOR]after loading the driver

---

### Post by tzorge on 2015-02-19
i got the following reply from the manufacturer although I cant make any sense of it.

[COLOR=#4A5571][FONT=Verdana]Hello,[/FONT][/COLOR]

[COLOR=#4A5571][FONT=Verdana]we never used the SAA716X Bridge in our Products.[/FONT][/COLOR]
[COLOR=#4A5571][FONT=Verdana]Seems there are worng dependencies, but not relatetd to our products.[/FONT][/COLOR]

[COLOR=#4A5571][FONT=Verdana]best regards[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2015-02-19
There are some compiler warnings related to the SAA716 module, but it still builds and it does not stop the entire build with an error.

---

