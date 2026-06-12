---
title: "problems getting sound card to work"
date: 2009-04-24
forum: Multimedia Software
---

### Post by blau2009 on 2009-04-24
I have a mobo with ICH southbridge AC97 audio, which uses the snd-intel8x0 module. Sound does not work at all. I am trying to install the drivers, following the guide in the 'Comprehensive Sound Problem Solutions Guide' : [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I am trying to compile the drivers using module-assistant but the build does not complete correctly, with the following output: 


for i in control postinst postrm ; do \
		if [ -f debian/$i.orig ]; then \
			mv -f debian/$i.orig debian/$i ; \
		fi ; \
	done
rm -f control-munge
make mrproper
make[1]: Entering directory `/usr/src/modules/alsa-driver'
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
rm -f configure-stamp
rm -f build-stamp
/usr/bin/make -f debian/rules binary-modules
make[1]: Entering directory `/usr/src/modules/alsa-driver'
CC="gcc" ./configure --prefix=/usr --with-kernel=/usr/src/linux --with-build=/usr/src/linux --with-moddir=/lib/modules/2.6.27-11-server/updates/alsa --with-sequencer=yes --with-isapnp=yes --with-debug=detect --with-cards="intel8x0"
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/modules/alsa-driver
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... /usr/src/linux
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.27-11-server
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.27-11-server/updates/alsa
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... verbose
checking for ISA support in kernel... yes
checking for processor type... i686
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.17
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... yes
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... yes
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... intel8x0
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
touch configure-stamp
/usr/bin/make  compile
make[2]: Entering directory `/usr/src/modules/alsa-driver'
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -puvf include/version.h include/sound/version.h
/usr/bin/make dep
make[3]: Entering directory `/usr/src/modules/alsa-driver'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #2 succeeded at 156 (offset -1 lines).
Hunk #3 succeeded at 168 (offset -1 lines).
Hunk #4 succeeded at 178 (offset -1 lines).
Hunk #5 succeeded at 209 (offset -1 lines).
Hunk #6 succeeded at 494 (offset -1 lines).
Hunk #7 succeeded at 534 with fuzz 2 (offset -1 lines).
Hunk #8 succeeded at 993 (offset -1 lines).
Hunk #9 succeeded at 1022 (offset -1 lines).
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 898 (offset -12 lines).
Hunk #3 succeeded at 914 (offset -12 lines).
Hunk #4 succeeded at 926 (offset -12 lines).
Hunk #5 succeeded at 980 (offset -12 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #4 succeeded at 1585 (offset -17 lines).
Hunk #5 succeeded at 2820 (offset -39 lines).
Hunk #6 succeeded at 2840 (offset -39 lines).
Hunk #7 succeeded at 2870 (offset -39 lines).
Hunk #8 succeeded at 2897 (offset -39 lines).
Hunk #9 succeeded at 2913 (offset -39 lines).
Hunk #10 succeeded at 2943 (offset -39 lines).
Hunk #11 succeeded at 3029 (offset -39 lines).
Hunk #12 succeeded at 3048 (offset -39 lines).
Hunk #13 succeeded at 3062 (offset -39 lines).
Hunk #14 succeeded at 3120 (offset -39 lines).
Hunk #15 succeeded at 3148 (offset -39 lines).
Hunk #16 succeeded at 3206 (offset -39 lines).
Hunk #17 succeeded at 3235 (offset -39 lines).
Hunk #18 succeeded at 3265 (offset -39 lines).
Hunk #19 succeeded at 3342 (offset -39 lines).
Hunk #20 succeeded at 3374 (offset -39 lines).
Hunk #21 succeeded at 3440 (offset -39 lines).
Hunk #22 succeeded at 3469 (offset -39 lines).
Hunk #23 succeeded at 3510 (offset -39 lines).
Hunk #24 succeeded at 3660 (offset -39 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #3 succeeded at 713 (offset -6 lines).
Hunk #4 succeeded at 776 (offset -10 lines).
Hunk #5 succeeded at 1384 (offset -10 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 277 (offset 13 lines).
Hunk #3 succeeded at 303 (offset 13 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1291 (offset 2 lines).
Hunk #4 succeeded at 1375 (offset 2 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 990 (offset -2 lines).
Hunk #4 succeeded at 1912 (offset -2 lines).
Hunk #5 succeeded at 1957 (offset -2 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
copying file alsa-kernel/core/misc.c
patching file misc.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 2589 (offset -1 lines).
Hunk #4 succeeded at 2640 (offset -1 lines).
Hunk #5 succeeded at 2763 (offset -1 lines).
Hunk #6 succeeded at 2946 (offset -1 lines).
Hunk #7 succeeded at 3073 (offset -1 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[5]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
make[6]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[6]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[4]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/l3'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/l3'
make[5]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[4]: Entering directory `/usr/src/modules/alsa-driver/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[5]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[4]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[5]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[5]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1669 (offset -2 lines).
Hunk #3 succeeded at 1714 (offset -2 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1309 (offset 2 lines).
Hunk #3 succeeded at 1352 (offset 2 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3131 (offset -45 lines).
Hunk #3 succeeded at 3426 (offset -45 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2119 (offset -12 lines).
Hunk #3 succeeded at 2495 (offset -12 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #2 succeeded at 1426 (offset 23 lines).
Hunk #3 succeeded at 1607 (offset 23 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #5 succeeded at 3140 (offset 12 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2439 (offset 3 lines).
Hunk #3 succeeded at 2449 (offset 3 lines).
Hunk #4 succeeded at 2464 (offset 3 lines).
Hunk #5 succeeded at 2475 (offset 3 lines).
Hunk #6 succeeded at 2486 (offset 3 lines).
Hunk #7 succeeded at 2569 (offset 3 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1182 (offset 2 lines).
Hunk #3 succeeded at 1242 (offset 2 lines).
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1912 (offset 1 line).
Hunk #4 succeeded at 1924 (offset 1 line).
Hunk #5 succeeded at 1948 (offset 1 line).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2207 (offset 2 lines).
Hunk #3 succeeded at 2377 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 340 (offset -1 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/aw2'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/aw2'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1365 (offset 12 lines).
Hunk #4 succeeded at 1734 (offset 12 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1898 (offset -28 lines).
Hunk #2 succeeded at 1961 (offset -28 lines).
copying file alsa-kernel/pci/echoaudio/darla20.c
patching file darla20.c
copying file alsa-kernel/pci/echoaudio/darla24.c
patching file darla24.c
copying file alsa-kernel/pci/echoaudio/echo3g.c
patching file echo3g.c
copying file alsa-kernel/pci/echoaudio/gina20.c
patching file gina20.c
copying file alsa-kernel/pci/echoaudio/gina24.c
patching file gina24.c
copying file alsa-kernel/pci/echoaudio/indigo.c
patching file indigo.c
copying file alsa-kernel/pci/echoaudio/indigodj.c
patching file indigodj.c
copying file alsa-kernel/pci/echoaudio/indigoio.c
patching file indigoio.c
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1406 (offset 1 line).
Hunk #5 succeeded at 1447 (offset 9 lines).
Hunk #6 succeeded at 1756 (offset 10 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 942 (offset 2 lines).
Hunk #3 succeeded at 1630 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #2 succeeded at 309 (offset 30 lines).
Hunk #3 succeeded at 347 (offset 30 lines).
Hunk #4 succeeded at 362 (offset 30 lines).
Hunk #5 succeeded at 378 (offset 30 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2352 (offset 3 lines).
Hunk #3 succeeded at 2513 (offset 3 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/oxygen'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/oxygen'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #3 succeeded at 2236 (offset 2 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2049 (offset 5 lines).
Hunk #3 succeeded at 2071 (offset 5 lines).
Hunk #4 succeeded at 2413 (offset 7 lines).
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[5]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[6]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[6]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[4]: Entering directory `/usr/src/modules/alsa-driver/soc'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/at32'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/at32'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/at91'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/at91'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/au1x'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/au1x'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/codecs'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/codecs'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/davinci'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/davinci'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/fsl'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/fsl'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/omap'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/omap'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/pxa'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/pxa'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/s3c24xx'
make[5]: Entering directory `/usr/src/modules/alsa-driver/soc/sh'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/soc/sh'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/soc'
make[4]: Entering directory `/usr/src/modules/alsa-driver/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #2 succeeded at 70 with fuzz 2.
Hunk #3 succeeded at 686 (offset 27 lines).
Hunk #4 succeeded at 713 (offset 27 lines).
Hunk #5 succeeded at 794 with fuzz 2 (offset 27 lines).
Hunk #6 succeeded at 809 with fuzz 2 (offset 27 lines).
Hunk #7 succeeded at 1183 with fuzz 1 (offset 23 lines).
Hunk #8 succeeded at 2112 (offset 30 lines).
Hunk #9 succeeded at 2131 (offset 30 lines).
Hunk #10 succeeded at 2143 (offset 30 lines).
Hunk #11 succeeded at 2156 (offset 30 lines).
Hunk #12 succeeded at 2736 (offset 49 lines).
Hunk #13 succeeded at 2808 (offset 49 lines).
Hunk #14 succeeded at 3096 (offset 49 lines).
Hunk #15 succeeded at 3167 (offset 49 lines).
Hunk #16 succeeded at 3288 (offset 49 lines).
Hunk #17 succeeded at 3306 (offset 49 lines).
Hunk #18 succeeded at 3320 (offset 49 lines).
Hunk #19 succeeded at 3333 (offset 49 lines).
Hunk #20 succeeded at 3536 (offset 48 lines).
Hunk #21 succeeded at 3629 (offset 48 lines).
Hunk #22 succeeded at 3767 (offset 49 lines).
Hunk #23 succeeded at 3828 (offset 49 lines).
Hunk #24 succeeded at 3847 (offset 49 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 227 (offset 2 lines).
Hunk #3 succeeded at 251 (offset 2 lines).
Hunk #4 succeeded at 350 (offset 8 lines).
Hunk #5 succeeded at 1465 (offset 103 lines).
Hunk #6 succeeded at 1814 (offset 108 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/caiaq'
copying file alsa-kernel/usb/caiaq/caiaq-audio.c
patching file caiaq-audio.c
Hunk #1 succeeded at 1 with fuzz 2.
Hunk #2 succeeded at 448 with fuzz 1 (offset -13 lines).
Hunk #3 succeeded at 511 (offset -8 lines).
copying file alsa-kernel/usb/caiaq/caiaq-device.c
patching file caiaq-device.c
Hunk #2 succeeded at 120 (offset 6 lines).
Hunk #3 succeeded at 370 (offset 6 lines).
copying file alsa-kernel/usb/caiaq/caiaq-input.c
patching file caiaq-input.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/caiaq'
make[5]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #11 succeeded at 1057 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[5]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[4]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[5]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[5]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[4]: Entering directory `/usr/src/modules/alsa-driver/misc'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/misc'
make[3]: Leaving directory `/usr/src/modules/alsa-driver'
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-11-server'
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_wrapper.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sgbuf.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_native.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_lib.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_misc.o
  CC [M]  /usr/src/modules/alsa-driver/acore/pcm_memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/timer.o
  CC [M]  /usr/src/modules/alsa-driver/acore/wrappers.o
  CC [M]  /usr/src/modules/alsa-driver/acore/misc_driver.o
  CC [M]  /usr/src/modules/alsa-driver/acore/memory_debug.o
  CC [M]  /usr/src/modules/alsa-driver/acore/sound.o
/usr/src/modules/alsa-driver/acore/sound.c: In function &#8216;snd_request_other&#8217;:
/usr/src/modules/alsa-driver/acore/sound.c:100: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/modules/alsa-driver/acore/init.o
/usr/src/modules/alsa-driver/acore/init.c: In function &#8216;snd_card_register&#8217;:
/usr/src/modules/alsa-driver/acore/init.c:568: warning: passing argument 5 of &#8216;device_create&#8217; makes pointer from integer without a cast
/usr/src/modules/alsa-driver/acore/init.c:568: warning: format not a string literal and no format arguments
  CC [M]  /usr/src/modules/alsa-driver/acore/memory.o
  CC [M]  /usr/src/modules/alsa-driver/acore/info.o
/usr/src/modules/alsa-driver/acore/info.c: In function &#8216;resize_info_buffer&#8217;:
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit declaration of function &#8216;PAGE_ALIGN&#8217;
make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-server'
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2

Can anyone help?

Thanks!

---

### Post by dino99 on 2009-04-24
hi,

could you give 'uname -a'
If you are running Jaunty, pulseaudio is the default sound driver. Check your settings in "system preference sound", and add in your sources.list: repo of medibuntu, update then whith synaptic install pavucontrol & pavumeter.

log out & in again, verify that sound is not on mute position !!!

IMHO you should not need to compile anything. Have a look at .xsessions.error (hidden file), and glance at /var/crash, /var/log

good luck :)

---

### Post by blau2009 on 2009-04-24
uname -a: 

Linux thebatcave 2.6.27-11-server #1 SMP Wed Apr 1 21:53:55 UTC 2009 i686 GNU/Linux

Running Ubuntu server 8.10

I install pavucontrol and pavumeter but it didn't help. When I added medibuntu, I get this error: 

Errors were encountered while processing:
 medibuntu-keyring
E: Sub-process /usr/bin/dpkg returned an error code (1)


I installed it using this command: 

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update


Thanks for the help... so far :D

---

### Post by blau2009 on 2009-04-24
OK fixed medibuntu, also upgraded to Ubuntu 9.04. I still get no audio using any output (pulse, alsa etc). Any other ideas?

Thanks

---

### Post by babuu on 2009-04-25
> **blau2009 said:**
> OK fixed medibuntu, also upgraded to Ubuntu 9.04. I still get no audio using any output (pulse, alsa etc). Any other ideas?

Thanks

Same here, upgraded to 9.04 and sound disappeared completely, doesnt matter if I try pulse or alsa. Have checked mixer levels with command alsamixer and all are fine.

The one thing I found in the syslog was this, don't know if this matters:

pulseaudio[4601]: module-console-kit.c: GetUnixUser() call failed: org.freedesktop.DBus.Error.UnknownMethod: Method "GetUnixUser" with signature "" on interface "org.freedesktop.ConsoleKit.Session" doesn't exist

---

### Post by blau2009 on 2009-04-26
Yep still can't get any sound. I've installed linux-backports-modules-jaunty as was suggested in another thread but it didn't help.

Now when I try to reconfigure alsa-source it lets me choose which module then just exits without any error messages. Is this because 9.04 is now using pulse be default?

Also I just installed Mythbuntu 9.04 on another box with Intel ICH onboard sound, it wasn't working on there either although I didn't try anything yet. It was working out of the box with 8.10

There must be a way to fix this, heaps of computers have the Intel ICH audio!

---

### Post by blau2009 on 2009-05-06
Got Pulse setup correctly I think, but it shows output in the pulse volume control for virtual output devices only. When I change to hardware devices, it shows none detected.

I reconfigured alsa with module assistant, it completes successfully but no luck.

I have the Realtek ALC655 on a Gigabyte GA-8IG1000MK mobo.

Absolutely stumped. Any suggestions to get sound working?

---

### Post by erikthedrink on 2009-09-08
Only if its an external device.  In Xubuntu, go to Applications, then Accessories, then Terminal.  In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

