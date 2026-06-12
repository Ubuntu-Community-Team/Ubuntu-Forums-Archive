---
title: "how can i get my sound back after a botched alsa install?"
date: 2011-06-29
forum: Multimedia Software
---

### Post by wim.glenn on 2011-06-29
hi all, 

i was having annoying sound issues on natty , with playback being randomly distorted , intermittently.  so i was trying to reinstall drivers for my sound (onboard hda-intel thing) , but i seem to have b0rked it because now i don't have any sound.  the volume control button now looks like "---" and if i click on "Sound Preferences..." i just get a hung dialog "Waiting for sound system to respond" with only a cancel button.  /proc/asound/ dir is gone.  here is what i did:

downloaded some LinuxPkg_5.16rc14.tar.bz2 which was supposed to be alsa driver for my hardware.  i unzipped that then followed the readme instructions:

tar xfvj alsa-driver-1.0.24-5.16rc14.tar.bz2
cd alsa-driver-1.0.24
./configure --with-cards=hda-intel
make
make install 

build seemed to go ok , but make install had some permissions denied stuff so i did 'sudo make install' instead, then rebooted my machine.  i saved a log of the build incase i would need to dig through it later.  



```
wim@wim-ubuntu:~/sandpit$ sudo ./install 
.....Decompress Driver source v1.0.24-5.16rc14
Compile Driver........
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
checking for current directory... /home/wim/sandpit/alsa-driver-1.0.24
checking cross compile... 
checking for directory with ALSA kernel sources... /home/wim/sandpit/alsa-driver-1.0.24/alsa-kernel
checking for directory with kernel source... /lib/modules/2.6.38-8-generic/build
checking for directory with kernel build... /lib/modules/2.6.38-8-generic/build
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.38-8-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for directory to store kernel modules... /lib/modules/2.6.38-8-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
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
checking for kernel linux/io.h... yes
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
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel linux/gfp.h... yes
checking for kernel pcmcia/cs_types.h... no
Creating <pcmcia/cs_types.h>...
checking for kernel pcmcia/cs.h... no
Creating <pcmcia/cs.h>...
checking for kernel trace/events/asoc.h... yes
checking for kernel linux/lzo.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
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
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... no
checking for V4L1 layer... no
checking for V4L2 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.24-5.16rc14
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for kernel linux/usb/audio-v2.h... yes
checking for kernel linux/usb/audio.h... yes
checking for valid v1 in linux/usb/audio.h... yes
checking for invalid v2 in linux/usb/audio.h... no
checking for valid linux/usb/audio-v2.h... no
Creating <linux/usb/audio-v2.h>...
checking for kernel linux/usb/ch9.h... yes
checking usb_alloc_coherent... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for pm_qos_request... yes
checking for static pm_qos_request... yes
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... hda-intel
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  'Makefile.conf.in' seems to ignore the --datarootdir setting
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
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
make dep
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/include'
make -C sound prepare
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/include/sound'
make .includes.tmp
make[4]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/include/sound'
make[4]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/include/sound'
make prepare2
make[4]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/include/sound'
cp ../../alsa-kernel/include/ac97_codec.h .
patch -p0 -i ac97_codec.patch ac97_codec.h
patching file ac97_codec.h
ln -s ../../alsa-kernel/include/aci.h
ln -s ../../alsa-kernel/include/ad1816a.h
ln -s ../../alsa-kernel/include/ad1843.h
ln -s ../../alsa-kernel/include/ak4113.h
ln -s ../../alsa-kernel/include/ak4114.h
ln -s ../../alsa-kernel/include/ak4117.h
ln -s ../../alsa-kernel/include/ak4531_codec.h
ln -s ../../alsa-kernel/include/ak4xxx-adda.h
ln -s ../../alsa-kernel/include/alc5623.h
ln -s ../../alsa-kernel/include/asequencer.h
ln -s ../../alsa-kernel/include/asound.h
ln -s ../../alsa-kernel/include/asound_fm.h
ln -s ../../alsa-kernel/include/asoundef.h
ln -s ../../alsa-kernel/include/atmel-abdac.h
ln -s ../../alsa-kernel/include/atmel-ac97c.h
ln -s ../../alsa-kernel/include/control.h
cp ../../alsa-kernel/include/core.h .
patch -p0 -i core.patch core.h
patching file core.h
ln -s ../../alsa-kernel/include/cs4231-regs.h
ln -s ../../alsa-kernel/include/cs46xx.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_scb_types.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_spos.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_task_types.h
ln -s ../../alsa-kernel/include/cs8403.h
ln -s ../../alsa-kernel/include/cs8427.h
ln -s ../../alsa-kernel/include/emu10k1.h
ln -s ../../alsa-kernel/include/emu10k1_synth.h
ln -s ../../alsa-kernel/include/emu8000.h
ln -s ../../alsa-kernel/include/emu8000_reg.h
ln -s ../../alsa-kernel/include/emux_legacy.h
ln -s ../../alsa-kernel/include/emux_synth.h
ln -s ../../alsa-kernel/include/es1688.h
ln -s ../../alsa-kernel/include/gus.h
ln -s ../../alsa-kernel/include/hda_hwdep.h
ln -s ../../alsa-kernel/include/hdsp.h
ln -s ../../alsa-kernel/include/hdspm.h
ln -s ../../alsa-kernel/include/hwdep.h
ln -s ../../alsa-kernel/include/i2c.h
ln -s ../../alsa-kernel/include/info.h
ln -s ../../alsa-kernel/include/initval.h
ln -s ../../alsa-kernel/include/jack.h
ln -s ../../alsa-kernel/include/l3.h
ln -s ../../alsa-kernel/include/max98088.h
ln -s ../../alsa-kernel/include/memalloc.h
ln -s ../../alsa-kernel/include/minors.h
ln -s ../../alsa-kernel/include/mixer_oss.h
ln -s ../../alsa-kernel/include/mpu401.h
ln -s ../../alsa-kernel/include/opl3.h
ln -s ../../alsa-kernel/include/opl4.h
ln -s ../../alsa-kernel/include/pcm-indirect.h
cp ../../alsa-kernel/include/pcm.h .
patch -p0 -i pcm.patch pcm.h
patching file pcm.h
Hunk #3 succeeded at 310 (offset 1 line).
Hunk #4 succeeded at 331 (offset 1 line).
Hunk #5 succeeded at 359 (offset 1 line).
Hunk #6 succeeded at 377 (offset 1 line).
Hunk #7 succeeded at 415 (offset 1 line).
Hunk #8 succeeded at 435 (offset 1 line).
ln -s ../../alsa-kernel/include/pcm_oss.h
ln -s ../../alsa-kernel/include/pcm_params.h
ln -s ../../alsa-kernel/include/pt2258.h
ln -s ../../alsa-kernel/include/pxa2xx-lib.h
ln -s ../../alsa-kernel/include/rawmidi.h
ln -s ../../alsa-kernel/include/s3c24xx_uda134x.h
ln -s ../../alsa-kernel/include/sb.h
ln -s ../../alsa-kernel/include/sb16_csp.h
ln -s ../../alsa-kernel/include/seq_device.h
ln -s ../../alsa-kernel/include/seq_kernel.h
ln -s ../../alsa-kernel/include/seq_midi_emul.h
ln -s ../../alsa-kernel/include/seq_midi_event.h
ln -s ../../alsa-kernel/include/seq_oss.h
ln -s ../../alsa-kernel/include/seq_oss_legacy.h
ln -s ../../alsa-kernel/include/seq_virmidi.h
ln -s ../../alsa-kernel/include/sfnt_info.h
ln -s ../../alsa-kernel/include/sh_dac_audio.h
ln -s ../../alsa-kernel/include/sh_fsi.h
ln -s ../../alsa-kernel/include/snd_wavefront.h
ln -s ../../alsa-kernel/include/soc-dai.h
ln -s ../../alsa-kernel/include/soc-dapm.h
ln -s ../../alsa-kernel/include/soc.h
ln -s ../../alsa-kernel/include/soundfont.h
ln -s ../../alsa-kernel/include/tea575x-tuner.h
ln -s ../../alsa-kernel/include/tea6330t.h
ln -s ../../alsa-kernel/include/timer.h
ln -s ../../alsa-kernel/include/tlv.h
ln -s ../../alsa-kernel/include/tlv320aic3x.h
ln -s ../../alsa-kernel/include/tlv320dac33-plat.h
ln -s ../../alsa-kernel/include/tpa6130a2-plat.h
ln -s ../../alsa-kernel/include/trident.h
ln -s ../../alsa-kernel/include/uda134x.h
ln -s ../../alsa-kernel/include/uda1380.h
ln -s ../../alsa-kernel/include/util_mem.h
ln -s ../version.h
ln -s ../../alsa-kernel/include/vx_core.h
ln -s ../../alsa-kernel/include/wavefront.h
ln -s ../../alsa-kernel/include/wm2000.h
ln -s ../../alsa-kernel/include/wm8903.h
ln -s ../../alsa-kernel/include/wm8904.h
ln -s ../../alsa-kernel/include/wm8955.h
ln -s ../../alsa-kernel/include/wm8960.h
ln -s ../../alsa-kernel/include/wm8962.h
ln -s ../../alsa-kernel/include/wm8993.h
ln -s ../../alsa-kernel/include/wm9081.h
ln -s ../../alsa-kernel/include/wm9090.h
ln -s ../../alsa-kernel/include/wss.h
ln -s ../../alsa-kernel/include/ymfpci.h
make[4]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/include/sound'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/include/sound'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/include'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore'
copying file alsa-kernel/core/info.c
patching file info.c
Hunk #4 succeeded at 495 (offset 12 lines).
Hunk #5 succeeded at 535 (offset 12 lines).
Hunk #6 succeeded at 951 (offset 12 lines).
Hunk #7 succeeded at 991 (offset 12 lines).
Hunk #8 succeeded at 1025 (offset 12 lines).
copying file alsa-kernel/core/pcm.c
patching file pcm.c
Hunk #2 succeeded at 951 (offset 22 lines).
Hunk #3 succeeded at 967 (offset 22 lines).
Hunk #4 succeeded at 979 (offset 22 lines).
Hunk #5 succeeded at 1035 (offset 22 lines).
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
copying file alsa-kernel/core/pcm_memory.c
patching file pcm_memory.c
Hunk #2 succeeded at 452 (offset 1 line).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #3 succeeded at 740 (offset 5 lines).
Hunk #4 succeeded at 800 (offset 5 lines).
Hunk #5 succeeded at 1392 (offset 5 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #3 succeeded at 308 (offset 1 line).
copying file alsa-kernel/core/init.c
patching file init.c
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #3 succeeded at 1267 (offset 4 lines).
Hunk #4 succeeded at 1322 (offset 4 lines).
Hunk #5 succeeded at 1412 (offset 4 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
Hunk #2 succeeded at 39 (offset -1 lines).
Hunk #3 succeeded at 50 (offset -1 lines).
Hunk #4 succeeded at 190 (offset -1 lines).
Hunk #5 succeeded at 277 (offset -1 lines).
Hunk #6 succeeded at 289 (offset -1 lines).
Hunk #7 succeeded at 306 (offset -1 lines).
Hunk #8 succeeded at 330 (offset -1 lines).
Hunk #9 succeeded at 385 (offset -1 lines).
Hunk #10 succeeded at 396 (offset -1 lines).
Hunk #11 succeeded at 422 (offset -1 lines).
Hunk #12 succeeded at 529 (offset -1 lines).
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #3 succeeded at 1000 (offset 3 lines).
Hunk #4 succeeded at 1920 (offset 4 lines).
Hunk #5 succeeded at 1966 (offset 4 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
copying file alsa-kernel/core/misc.c
patching file misc.c
Hunk #2 succeeded at 49 (offset 1 line).
Hunk #3 succeeded at 150 (offset 1 line).
copying file alsa-kernel/core/hrtimer.c
patching file hrtimer.c
Hunk #2 succeeded at 67 (offset 1 line).
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/ioctl32'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/ioctl32'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #3 succeeded at 1920 (offset 5 lines).
Hunk #4 succeeded at 2645 (offset 5 lines).
Hunk #5 succeeded at 2697 (offset 5 lines).
Hunk #6 succeeded at 2825 (offset 5 lines).
Hunk #7 succeeded at 3010 (offset 5 lines).
Hunk #8 succeeded at 3138 (offset 5 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/oss'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #2 succeeded at 60 (offset 3 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 250 (offset 2 lines).
make[4]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
make[4]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/l3'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/l3'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/other'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/other'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers'
copying file alsa-kernel/drivers/mts64.c
patching file mts64.c
Hunk #2 succeeded at 835 (offset 1 line).
Hunk #3 succeeded at 1094 (offset 1 line).
copying file alsa-kernel/drivers/portman2x4.c
patching file portman2x4.c
Hunk #2 succeeded at 612 (offset 1 line).
Hunk #3 succeeded at 883 (offset 1 line).
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/mpu401'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #2 succeeded at 438 (offset 2 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl3'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl4'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl4'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/pcsp'
copying file alsa-kernel/drivers/pcsp/pcsp.c
patching file pcsp.c
copying file alsa-kernel/drivers/pcsp/pcsp_input.c
patching file pcsp_input.c
copying file alsa-kernel/drivers/pcsp/pcsp_lib.c
patching file pcsp_lib.c
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/pcsp'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/vx'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/vx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1816a'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1816a'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1848'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1848'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/cs423x'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/cs423x'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/es1688'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/es1688'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/galaxy'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/galaxy'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/gus'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/gus'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/msnd'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/msnd'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/opti9xx'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/opti9xx'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/sb'
copying file alsa-kernel/isa/sb/sb16_csp.c
patching file sb16_csp.c
Hunk #2 succeeded at 712 (offset 2 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/sb'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wavefront'
copying file alsa-kernel/isa/wavefront/wavefront_fx.c
patching file wavefront_fx.c
Hunk #2 succeeded at 251 (offset -3 lines).
copying file alsa-kernel/isa/wavefront/wavefront_synth.c
patching file wavefront_synth.c
Hunk #2 succeeded at 1947 (offset 1 line).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wavefront'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wss'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wss'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/synth'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/synth/emux'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/synth/emux'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/synth'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
copying file alsa-kernel/pci/atiixp.c
patching file atiixp.c
Hunk #2 succeeded at 1680 (offset 9 lines).
Hunk #3 succeeded at 1725 (offset 9 lines).
copying file alsa-kernel/pci/atiixp_modem.c
patching file atiixp_modem.c
Hunk #2 succeeded at 1313 (offset 6 lines).
Hunk #3 succeeded at 1356 (offset 6 lines).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #2 succeeded at 844 (offset -2 lines).
Hunk #3 succeeded at 998 (offset -2 lines).
copying file alsa-kernel/pci/cmipci.c
patching file cmipci.c
Hunk #2 succeeded at 3135 (offset -41 lines).
Hunk #3 succeeded at 3430 (offset -41 lines).
copying file alsa-kernel/pci/ens1370.c
patching file ens1370.c
Hunk #2 succeeded at 2121 (offset -10 lines).
Hunk #3 succeeded at 2497 (offset -10 lines).
copying file alsa-kernel/pci/fm801.c
patching file fm801.c
Hunk #3 succeeded at 1434 (offset 5 lines).
Hunk #4 succeeded at 1624 (offset 14 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #3 succeeded at 715 (offset 9 lines).
Hunk #4 succeeded at 725 (offset 9 lines).
Hunk #5 succeeded at 3300 (offset 172 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #2 succeeded at 2721 (offset 125 lines).
Hunk #3 succeeded at 2918 (offset 136 lines).
copying file alsa-kernel/pci/via82xx.c
patching file via82xx.c
Hunk #2 succeeded at 2505 (offset 11 lines).
Hunk #3 succeeded at 2515 (offset 11 lines).
Hunk #4 succeeded at 2530 (offset 11 lines).
Hunk #5 succeeded at 2541 (offset 11 lines).
Hunk #6 succeeded at 2552 (offset 11 lines).
Hunk #7 succeeded at 2635 (offset 11 lines).
copying file alsa-kernel/pci/via82xx_modem.c
patching file via82xx_modem.c
Hunk #2 succeeded at 1187 (offset 7 lines).
Hunk #3 succeeded at 1247 (offset 7 lines).
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #3 succeeded at 1927 (offset 9 lines).
Hunk #4 succeeded at 1939 (offset 9 lines).
Hunk #5 succeeded at 1963 with fuzz 1 (offset 9 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ac97'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ali5451'
copying file alsa-kernel/pci/ali5451/ali5451.c
patching file ali5451.c
Hunk #2 succeeded at 2148 (offset -57 lines).
Hunk #3 succeeded at 2318 (offset -57 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ali5451'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/asihpi'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/asihpi'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/au88x0'
copying file alsa-kernel/pci/au88x0/au88x0.c
patching file au88x0.c
Hunk #2 succeeded at 339 (offset -2 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/au88x0'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/aw2'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/aw2'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ca0106'
copying file alsa-kernel/pci/ca0106/ca0106_main.c
patching file ca0106_main.c
Hunk #3 succeeded at 1686 (offset 123 lines).
Hunk #4 succeeded at 1958 (offset 133 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ca0106'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs46xx'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs46xx'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs5535audio'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs5535audio'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ctxfi'
copying file alsa-kernel/pci/ctxfi/ctatc.c
patching file ctatc.c
Hunk #2 succeeded at 1238 (offset -10 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ctxfi'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/echoaudio'
copying file alsa-kernel/pci/echoaudio/echoaudio.c
patching file echoaudio.c
Hunk #1 succeeded at 1945 (offset 2 lines).
Hunk #2 succeeded at 2017 (offset 2 lines).
Hunk #3 succeeded at 2252 (offset 1 line).
Hunk #4 succeeded at 2262 (offset 3 lines).
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
copying file alsa-kernel/pci/echoaudio/indigodjx.c
patching file indigodjx.c
Hunk #2 succeeded at 112 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/indigoiox.c
patching file indigoiox.c
Hunk #2 succeeded at 114 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/layla20.c
patching file layla20.c
copying file alsa-kernel/pci/echoaudio/layla24.c
patching file layla24.c
copying file alsa-kernel/pci/echoaudio/mia.c
patching file mia.c
Hunk #2 succeeded at 125 (offset 1 line).
copying file alsa-kernel/pci/echoaudio/mona.c
patching file mona.c
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/echoaudio'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/emu10k1'
copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1409 (offset -1 lines).
Hunk #5 succeeded at 1452 (offset -1 lines).
Hunk #6 succeeded at 1767 (offset 3 lines).
copying file alsa-kernel/pci/emu10k1/emu10k1x.c
patching file emu10k1x.c
Hunk #2 succeeded at 941 (offset 1 line).
Hunk #3 succeeded at 1634 (offset 6 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/emu10k1'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/hda'
copying file alsa-kernel/pci/hda/hda_intel.c
patching file hda_intel.c
Hunk #2 succeeded at 2403 (offset 50 lines).
Hunk #3 succeeded at 2420 (offset 52 lines).
Hunk #4 succeeded at 2436 (offset 52 lines).
Hunk #5 succeeded at 2449 (offset 52 lines).
Hunk #6 succeeded at 2571 (offset 53 lines).
copying file alsa-kernel/pci/hda/hda_beep.c
patching file hda_beep.c
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/hda'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ice1712'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ice1712'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/korg1212'
copying file alsa-kernel/pci/korg1212/korg1212.c
patching file korg1212.c
Hunk #2 succeeded at 2344 (offset 5 lines).
Hunk #3 succeeded at 2500 (offset 5 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/korg1212'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/lx6464es'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/lx6464es'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/mixart'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/mixart'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/nm256'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/nm256'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/oxygen'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/oxygen'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pcxhr'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pcxhr'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pdplus'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pdplus'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #2 succeeded at 1237 (offset -1 lines).
Hunk #3 succeeded at 2226 (offset 8 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/riptide'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/rme9652'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/rme9652'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/trident'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/trident'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/vx222'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/vx222'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ymfpci'
copying file alsa-kernel/pci/ymfpci/ymfpci_main.c
patching file ymfpci_main.c
Hunk #2 succeeded at 2020 (offset -6 lines).
Hunk #3 succeeded at 2040 (offset -6 lines).
Hunk #4 succeeded at 2380 (offset -6 lines).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ymfpci'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/codecs'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/codecs'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/core'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/core'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/fabrics'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/fabrics'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus'
make[4]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc'
copying file alsa-kernel/soc/soc-core.c
patching file soc-core.c
Hunk #2 succeeded at 1481 (offset -20 lines).
Hunk #3 succeeded at 1955 (offset -18 lines).
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/atmel'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/atmel'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/au1x'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/au1x'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/blackfin'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/blackfin'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/codecs'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/codecs'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/davinci'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/davinci'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/ep93xx'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/ep93xx'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/fsl'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/fsl'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/imx'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/imx'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/jz4740'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/jz4740'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/kirkwood'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/kirkwood'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/mid-x86'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/mid-x86'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/nuc900'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/nuc900'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/omap'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/omap'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/pxa'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/pxa'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/s6000'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/s6000'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/samsung'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/samsung'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/sh'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/sh'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/tegra'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/tegra'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/txx9'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/txx9'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb'
copying file alsa-kernel/usb/card.c
patching file card.c
copying file alsa-kernel/usb/endpoint.c
patching file endpoint.c
Hunk #2 succeeded at 261 (offset 76 lines).
Hunk #3 succeeded at 375 (offset 99 lines).
Hunk #4 succeeded at 395 (offset 88 lines).
copying file alsa-kernel/usb/helper.c
patching file helper.c
Hunk #2 succeeded at 93 (offset 1 line).
copying file alsa-kernel/usb/quirks.c
patching file quirks.c
Hunk #2 succeeded at 162 (offset 3 lines).
Hunk #3 succeeded at 237 (offset 3 lines).
Hunk #4 succeeded at 327 (offset 4 lines).
Hunk #5 succeeded at 345 (offset 4 lines).
Hunk #6 succeeded at 359 (offset 4 lines).
Hunk #7 succeeded at 372 (offset 4 lines).
copying file alsa-kernel/usb/urb.c
patching file urb.c
Hunk #2 succeeded at 72 (offset 1 line).
Hunk #3 succeeded at 87 (offset 1 line).
Hunk #4 succeeded at 171 (offset 1 line).
Hunk #5 succeeded at 198 (offset 1 line).
Hunk #6 succeeded at 351 (offset 2 lines).
copying file alsa-kernel/usb/midi.c
patching file midi.c
Hunk #9 succeeded at 1861 (offset 1 line).
Hunk #10 succeeded at 2239 (offset 1 line).
copying file alsa-kernel/usb/mixer.c
patching file mixer.c
Hunk #2 succeeded at 113 (offset -17 lines).
Hunk #3 succeeded at 2064 (offset 41 lines).
Hunk #4 succeeded at 2138 (offset 41 lines).
copying file alsa-kernel/usb/mixer_quirks.c
patching file mixer_quirks.c
Hunk #2 succeeded at 65 (offset 2 lines).
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/6fire'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/6fire'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/caiaq'
copying file alsa-kernel/usb/caiaq/audio.c
patching file audio.c
Hunk #2 succeeded at 610 (offset 146 lines).
Hunk #3 succeeded at 673 (offset 146 lines).
copying file alsa-kernel/usb/caiaq/device.c
patching file device.c
Hunk #2 succeeded at 145 (offset 13 lines).
Hunk #3 succeeded at 401 (offset 7 lines).
copying file alsa-kernel/usb/caiaq/input.c
patching file input.c
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/caiaq'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/misc'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/misc'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
Hunk #2 succeeded at 33 (offset 1 line).
Hunk #3 succeeded at 56 (offset 1 line).
Hunk #4 succeeded at 142 (offset 1 line).
Hunk #5 succeeded at 181 (offset 1 line).
Hunk #6 succeeded at 237 (offset 1 line).
Hunk #7 succeeded at 290 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
Hunk #2 succeeded at 174 (offset 1 line).
Hunk #3 succeeded at 190 (offset 1 line).
Hunk #4 succeeded at 254 (offset 1 line).
Hunk #5 succeeded at 267 (offset 1 line).
Hunk #6 succeeded at 313 (offset 1 line).
Hunk #7 succeeded at 377 (offset 1 line).
Hunk #8 succeeded at 401 (offset 1 line).
Hunk #9 succeeded at 427 (offset 1 line).
Hunk #10 succeeded at 448 (offset 1 line).
Hunk #11 succeeded at 508 (offset 1 line).
Hunk #12 succeeded at 528 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
Hunk #2 succeeded at 69 (offset 1 line).
Hunk #3 succeeded at 317 (offset 1 line).
Hunk #4 succeeded at 350 (offset 1 line).
Hunk #5 succeeded at 366 (offset 1 line).
Hunk #6 succeeded at 392 (offset 1 line).
Hunk #7 succeeded at 408 (offset 1 line).
Hunk #8 succeeded at 525 (offset 1 line).
Hunk #9 succeeded at 548 (offset 1 line).
Hunk #10 succeeded at 697 (offset 1 line).
Hunk #11 succeeded at 1061 (offset 1 line).
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
Hunk #2 succeeded at 153 (offset 1 line).
Hunk #3 succeeded at 233 (offset 1 line).
Hunk #4 succeeded at 267 (offset 1 line).
Hunk #5 succeeded at 307 (offset 1 line).
Hunk #6 succeeded at 328 (offset 1 line).
Hunk #7 succeeded at 454 (offset 1 line).
Hunk #8 succeeded at 482 (offset 1 line).
Hunk #9 succeeded at 715 (offset 1 line).
Hunk #10 succeeded at 728 (offset 1 line).
Hunk #11 succeeded at 803 (offset 1 line).
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/usx2y'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/vx'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/vx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/wim/sandpit/alsa-driver-1.0.24  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/hwdep.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/memory_wrapper.o
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memory_wrapper.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/memalloc.o
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memalloc.inc:1,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memalloc.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memalloc.inc:1,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memalloc.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/sgbuf.o
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/sgbuf.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/pcm.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/pcm_native.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/pcm_lib.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/pcm_timer.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/pcm_misc.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/pcm_memory.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/timer.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/wrappers.o
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/wrappers.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/misc_driver.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/sound.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/init.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/memory.o
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memory.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
In file included from /home/wim/sandpit/alsa-driver-1.0.24/include/linux/config.h:4:0,
                 from /home/wim/sandpit/alsa-driver-1.0.24/include/alsa-autoconf.h:9,
                 from /home/wim/sandpit/alsa-driver-1.0.24/acore/memory.c:1:
/home/wim/sandpit/alsa-driver-1.0.24/include/generated/autoconf.h:4372:0: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2251:0: note: this is the location of the previous definition
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/info.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/control.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/misc.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/device.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/isadma.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/sound_oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/info_oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/vmaster.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/jack.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-hwdep.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-timer.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-pcm.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-page-alloc.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/mixer_oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/pcm_oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/pcm_plugin.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/io.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/copy.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/linear.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/mulaw.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/route.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/rate.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/snd-mixer-oss.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/snd-pcm-oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_device.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_midi_event.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_lock.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_clientmgr.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_memory.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_queue.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_fifo.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_prioq.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_timer.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_system.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_ports.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/seq_info.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq-device.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq-midi-event.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_init.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_timer.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_ioctl.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_event.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_rw.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_synth.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_midi.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_readq.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/seq_oss_writeq.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/snd-seq-oss.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_analog.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/dummy.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_ca0110.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_cirrus.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_cmedia.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_conexant.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_hdmi.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_eld.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_sigmatel.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_realtek.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_si3054.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/patch_via.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_codec.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_generic.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_proc.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_hwdep.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_beep.o
  CC [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/hda_intel.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-realtek.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cmedia.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-analog.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-idt.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-si3054.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cirrus.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-ca0110.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-conexant.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-via.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-hdmi.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-intel.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-atihdmi.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-intelhdmi.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-nvhdmi.o
  Building modules, stage 2.
  MODPOST 26 modules
WARNING: "register_sound_special_device" [/home/wim/sandpit/alsa-driver-1.0.24/acore/snd.ko] undefined!
WARNING: "unregister_sound_special" [/home/wim/sandpit/alsa-driver-1.0.24/acore/snd.ko] undefined!
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/snd-mixer-oss.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/snd-mixer-oss.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/snd-pcm-oss.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/oss/snd-pcm-oss.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/snd-seq-oss.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss/snd-seq-oss.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq-device.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq-device.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq-midi-event.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq-midi-event.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/seq/snd-seq.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-hwdep.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-hwdep.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-page-alloc.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-page-alloc.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-pcm.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-pcm.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-timer.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd-timer.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/acore/snd.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/acore/snd.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-analog.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-analog.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-atihdmi.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-atihdmi.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-ca0110.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-ca0110.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cirrus.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cirrus.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cmedia.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-cmedia.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-conexant.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-conexant.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-hdmi.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-hdmi.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-idt.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-idt.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-intelhdmi.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-intelhdmi.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-nvhdmi.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-nvhdmi.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-realtek.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-realtek.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-si3054.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-si3054.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-via.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec-via.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-codec.ko
  CC      /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-intel.mod.o
  LD [M]  /home/wim/sandpit/alsa-driver-1.0.24/pci/hda/snd-hda-intel.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
utils/link-modules /home/wim/sandpit/alsa-driver-1.0.24

ALSA modules were successfully compiled.

if [ -L /usr/include/sound ]; then \
		rm -f /usr/include/sound; \
		ln -sf /home/wim/sandpit/alsa-driver-1.0.24/include/sound /usr/include/sound; \
	else \
		rm -rf /usr/include/sound; \
		install -d -m 755 -g root -o root /usr/include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /usr/include/sound; \
		done \
	fi
find /lib/modules/2.6.38-8-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.38-8-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.38-8-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.38-8-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/include'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore'
mkdir -p /lib/modules/2.6.38-8-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.38-8-generic/kernel/sound/acore
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/ioctl32'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/ioctl32'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/oss'
mkdir -p /lib/modules/2.6.38-8-generic/kernel/sound/acore/oss
cp snd-mixer-oss.ko snd-pcm-oss.ko /lib/modules/2.6.38-8-generic/kernel/sound/acore/oss
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/oss'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq'
mkdir -p /lib/modules/2.6.38-8-generic/kernel/sound/acore/seq
cp snd-seq-device.ko snd-seq-midi-event.ko snd-seq.ko /lib/modules/2.6.38-8-generic/kernel/sound/acore/seq
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss'
mkdir -p /lib/modules/2.6.38-8-generic/kernel/sound/acore/seq/oss
cp snd-seq-oss.ko /lib/modules/2.6.38-8-generic/kernel/sound/acore/seq/oss
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq/oss'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore/seq'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/acore'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/l3'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/l3'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/other'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c/other'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/i2c'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/mpu401'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/mpu401'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl3'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl3'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl4'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/opl4'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/pcsp'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/pcsp'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/vx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers/vx'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/drivers'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1816a'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1816a'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1848'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/ad1848'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/cs423x'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/cs423x'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/es1688'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/es1688'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/galaxy'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/galaxy'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/gus'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/gus'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/msnd'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/msnd'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/opti9xx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/opti9xx'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/sb'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/sb'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wavefront'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wavefront'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wss'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa/wss'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/isa'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/synth'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/synth/emux'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/synth/emux'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/synth'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ac97'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ac97'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ali5451'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ali5451'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/asihpi'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/asihpi'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/au88x0'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/au88x0'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/aw2'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/aw2'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ca0106'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ca0106'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs46xx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs46xx'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs5535audio'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/cs5535audio'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ctxfi'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ctxfi'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/echoaudio'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/echoaudio'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/emu10k1'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/emu10k1'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/hda'
mkdir -p /lib/modules/2.6.38-8-generic/kernel/sound/pci/hda
cp snd-hda-codec-analog.ko snd-hda-codec-atihdmi.ko snd-hda-codec-ca0110.ko snd-hda-codec-cirrus.ko snd-hda-codec-cmedia.ko snd-hda-codec-conexant.ko snd-hda-codec-hdmi.ko snd-hda-codec-idt.ko snd-hda-codec-intelhdmi.ko snd-hda-codec-nvhdmi.ko snd-hda-codec-realtek.ko snd-hda-codec-si3054.ko snd-hda-codec-via.ko snd-hda-codec.ko snd-hda-intel.ko /lib/modules/2.6.38-8-generic/kernel/sound/pci/hda
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/hda'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ice1712'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ice1712'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/korg1212'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/korg1212'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/lx6464es'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/lx6464es'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/mixart'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/mixart'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/nm256'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/nm256'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/oxygen'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/oxygen'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pcxhr'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pcxhr'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pdplus'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/pdplus'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/riptide'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/riptide'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/rme9652'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/rme9652'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/trident'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/trident'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/vx222'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/vx222'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ymfpci'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci/ymfpci'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pci'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/codecs'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/codecs'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/core'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/core'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/fabrics'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/fabrics'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus'
make[3]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus/i2sbus'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa/soundbus'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/aoa'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/atmel'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/atmel'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/au1x'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/au1x'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/blackfin'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/blackfin'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/codecs'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/codecs'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/davinci'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/davinci'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/ep93xx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/ep93xx'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/fsl'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/fsl'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/imx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/imx'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/jz4740'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/jz4740'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/kirkwood'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/kirkwood'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/mid-x86'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/mid-x86'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/nuc900'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/nuc900'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/omap'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/omap'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/pxa'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/pxa'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/s6000'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/s6000'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/samsung'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/samsung'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/sh'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/sh'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/tegra'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/tegra'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/txx9'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc/txx9'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/soc'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/6fire'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/6fire'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/caiaq'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/caiaq'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/misc'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/misc'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/usx2y'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb/usx2y'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/usb'
make[1]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/pdaudiocf'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/pdaudiocf'
make[2]: Entering directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/vx'
make[2]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia/vx'
make[1]: Leaving directory `/home/wim/sandpit/alsa-driver-1.0.24/pcmcia'
/sbin/depmod -a 2.6.38-8-generic 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
rm: cannot remove `/dev/snd': Is a directory
rm: cannot remove `/dev/snd/by-id': Is a directory
rm: cannot remove `/dev/snd/by-path': Is a directory
rmdir: failed to remove `/dev/snd': Directory not empty
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
bzip2: Output file test.wav already exists.
bzip2: Output file test.wav.bz2 already exists.
Remove Folder.....
./install: 48: alsaconf: not found
wim@wim-ubuntu:~/sandpit$ 

```


what can i do to get my sound working properly, or at least to get it back into the half-broken state like it was before i b0rked it even more?   :(

---

### Post by handy on 2011-06-29
Either of these may help you:

[http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)

[http://ubuntuforums.org/showthread.php?p=10942458#post10942458](http://ubuntuforums.org/showthread.php?p=10942458#post10942458)

---

### Post by gylti on 2011-06-29
Iv just posted a thread above just to let people know how I got sound in Runescape (a java online game) using an alsa compatibility package it may help you a bit. Im not an expert just dont like being beaten by a computer took me 4 months to solve my problem

I also lost my kernel file and couldnt boot so upgraded from the dos screen to 11.04  when it prompted me - i was using 10:10 till then when i messed up

---

### Post by wolfen69 on 2011-06-29
You could also try installing module assistant and
```
sudo m-a a-i alsa
```
then
```
sudo modprobe alsa
```
you *may* need a reboot.

---

### Post by wim.glenn on 2011-06-30
wolfen69 thanks for the suggestions, i've tried sudo m-a a-i alsa , and it fails here: 

```
/usr/src/modules/alsa-driver/include/linux/pci_ids.h:2:58: fatal error: @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory
```

the strange thing is, i do have the file.. although it is a symbolic link:
```
wim@wim-ubuntu:/usr/src/modules/alsa-driver/include/linux$ ls pci_ids.h 
lrwxrwxrwx 1 src 19 2011-06-30 20:05 pci_ids.h -> ../pci_ids_compat.h
```

what could i try to fix that?

---

### Post by wim.glenn on 2011-06-30
twimc,  i was able to get sound back with the following method:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

---

