---
title: "Compile ALSA -- does not work"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by Timokl on 2007-05-19
Hi,

I tinkered with my ALSA driver which worked previously for playback (although not for recording), and now, I cannot use my soundcard (Realtek AC'97, access through atiixp driver before) through ALSA any more (although OSS still works).

I followed the instructions in [doc.gwos.org...Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide"), and I tried to purge n' install alsa-base (no success!), so I wanted to build everything from the source, as explained in above website, point 4.

Here's the compilation process up to the errors:

```
**timo@aristoteles:/usr/src/modules/alsa-driver$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=atiixp --with-oss=yes**
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
checking for directory with kernel source... /usr/src/linux-headers-2.6.20-15-generic
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.20-15-generic
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
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
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.20-15-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
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
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... atiixp
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
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
**timo@aristoteles:/usr/src/modules/alsa-driver$ sudo make**
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -auvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/src/modules/alsa-driver'
make[2]: Entering directory `/usr/src/modules/alsa-driver/acore'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/ioctl32'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/oss'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/oss'
make[3]: Entering directory `/usr/src/modules/alsa-driver/acore/seq'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/instr'
make[4]: Entering directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq/oss'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/acore/seq'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/acore'
make[2]: Entering directory `/usr/src/modules/alsa-driver/i2c'
make[3]: Entering directory `/usr/src/modules/alsa-driver/i2c/other'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/i2c/other'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/i2c'
make[2]: Entering directory `/usr/src/modules/alsa-driver/drivers'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/mpu401'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl3'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/opl4'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/pcsp'
make[3]: Entering directory `/usr/src/modules/alsa-driver/drivers/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/drivers/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/drivers'
make[2]: Entering directory `/usr/src/modules/alsa-driver/isa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1816a'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/ad1848'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/cs423x'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/es1688'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/gus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/msnd'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/opti9xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/sb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/isa/wavefront'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/isa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/synth'
make[3]: Entering directory `/usr/src/modules/alsa-driver/synth/emux'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pci'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ac97'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ali5451'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/asihpi'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/au88x0'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ca0106'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs46xx'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/cs5535audio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/echoaudio'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/emu10k1'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/hda'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/hda'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ice1712'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/korg1212'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/mixart'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/nm256'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pcxhr'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/pdplus'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/riptide'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/riptide'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/rme9652'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/trident'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/vx222'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pci/ymfpci'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pci'
make[2]: Entering directory `/usr/src/modules/alsa-driver/aoa'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/codecs'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/core'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/core'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/fabrics'
make[3]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[4]: Entering directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/aoa/soundbus'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/aoa'
make[2]: Entering directory `/usr/src/modules/alsa-driver/usb'
make[3]: Entering directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/usb/usx2y'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/usb'
make[2]: Entering directory `/usr/src/modules/alsa-driver/pcmcia'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[3]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia/vx'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/pcmcia'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/usr/src/modules/alsa-driver  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: **error:** linux/config.h: No such file or directory
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h:742: **error**: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: **error**: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/modules/alsa-driver/include/adriver.h:761: **error**: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: **error**: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/modules/alsa-driver/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/modules/alsa-driver/include/adriver.h:1103: **error: too many arguments to function ‘pci_restore_state’**
make[3]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] **Error 1**
make[2]: *** [/usr/src/modules/alsa-driver/acore] **Error 2**
make[1]: *** [_module_/usr/src/modules/alsa-driver] **Error 2**
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] **Error 2**

```

As far as I understand, there seem to be some files missing, but where can I get them?

Bye,
Timo

---

### Post by icechen1 on 2007-05-20
I am having that issue too,but here is a fix i found:
[http://ubuntuforums.org/showpost.php?p=2691849&postcount=2](http://ubuntuforums.org/showpost.php?p=2691849&postcount=2)

---

### Post by Timokl on 2007-05-21
Yes, that solved my problem! Thnx a lot!

---

