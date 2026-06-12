---
title: "Cannot compile audio drivers for intel chipset(Following Comprehensive Sound Problem)"
date: 2008-12-18
forum: Multimedia Software
---

### Post by atarbann on 2008-12-18
Hello there

I been trying to set my 

"00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
"

audio device:

I have followed the instructions in the " Comprehensive Sound Problem Solutions Guide " thread, the alsa-source and the alsa project.

I think i have problems with my gcc compiler, exactly in sudo ./configure and sudo make (i have used the --with add).

This is the output

nicolas@Ingeamco5:/usr/src/alsa/alsa-driver-1.0.14$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.14
checking cross compile... 
checking for directory with kernel source... /usr/src/linux-headers-2.6.27-9-generic
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.27-9-generic
checking for GCC version... ./configure: eval: line 4855: syntax error near unexpected token `)'
./configure: eval: line 4855: `my_compiler_version=4.3.2-1ubuntu11)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking to modify of kernel linux/kmod.h... no
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
checking for kernel linux/latency.h... no
Creating <linux/latency.h>...
checking for kernel asm/irq_regs.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.27-9-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
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
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... yes
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.14
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... no
checking for gfp_t... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
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
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...

nicolas@Ingeamco5:/usr/src/alsa/alsa-driver-1.0.14$ sudo make
make dep
make[1]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/acore'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/ioctl32'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/ioctl32'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/oss'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/oss'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/seq'
make[4]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/seq/instr'
make[4]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/seq/instr'
make[4]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/seq/oss'
make[4]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/seq/oss'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/acore/seq'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/acore'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/i2c'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/i2c/other'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/i2c/other'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/i2c'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/mpu401'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/mpu401'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/opl3'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/opl3'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/opl4'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/opl4'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/pcsp'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/pcsp'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/vx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers/vx'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/drivers'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/ad1816a'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/ad1816a'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/ad1848'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/ad1848'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/cs423x'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/cs423x'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/es1688'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/es1688'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/gus'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/gus'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/msnd'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/msnd'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/opti9xx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/opti9xx'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/sb'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/sb'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/wavefront'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa/wavefront'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/isa'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/synth'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/synth/emux'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/synth/emux'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/synth'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ac97'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ac97'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ali5451'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ali5451'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/asihpi'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/asihpi'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/au88x0'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/au88x0'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ca0106'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ca0106'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/cs46xx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/cs46xx'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/echoaudio'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/echoaudio'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/emu10k1'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/emu10k1'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/hda'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/hda'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ice1712'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ice1712'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/korg1212'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/korg1212'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/mixart'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/mixart'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/nm256'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/nm256'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/pcxhr'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/pcxhr'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/pdplus'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/pdplus'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/riptide'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/riptide'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/rme9652'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/rme9652'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/trident'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/trident'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/vx222'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/vx222'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ymfpci'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci/ymfpci'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pci'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/codecs'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/codecs'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/core'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/core'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/fabrics'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/fabrics'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/soundbus'
make[4]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[4]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa/soundbus'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/aoa'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/soc'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/at91'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/at91'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/codecs'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/codecs'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/pxa'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/pxa'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/sh'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/soc/sh'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/soc'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/usb'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/usb/caiaq'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/usb/caiaq'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/usb/usx2y'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/usb/usx2y'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/usb'
make[2]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pcmcia'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: se ingresa al directorio `/usr/src/alsa/alsa-driver-1.0.14/pcmcia/vx'
make[3]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pcmcia/vx'
make[2]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14/pcmcia'
make[1]: se sale del directorio `/usr/src/alsa/alsa-driver-1.0.14'
make -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/alsa/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.27-9-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Alto.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.14] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [compile] Error 2


Y hope u can give me any hint ... because i have not any left.

---

### Post by markbuntu on 2008-12-18
First of all, that OP has not been updated for over 2 years and alsa 1.0.14 has no support for your sound card anyway so don't bother with trying to compile it.

Sometimes I wonder why that is a sticky.

There is more up to date help for you here.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

In **Drivers** there is a HDA section, follow those links.

---

