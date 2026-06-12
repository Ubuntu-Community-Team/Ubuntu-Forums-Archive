---
title: "Difficulty installing Linuxant ALSA driver"
date: 2010-10-10
forum: Multimedia Software
---

### Post by CarpKing on 2010-10-10
I am attempting to install the Linuxant ALSA driver to make my sound work properly (speakers muting when headphones plugged in).  This worked on Lucid, but on Maverick the installation fails at the "building modules" stage.  It directs me to a logfile, which I have reproduced here:

```
rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
echo skipping rm -f alsa-kernel/include/version.h
skipping rm -f alsa-kernel/include/version.h
rm -fr .tmp_versions
rm -f Module.symvers
find include/sound -name "*.h" -type l | xargs rm -f
rm -fr include/generated
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
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
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.35-22-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.35-22-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

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
checking for directory to store kernel modules... /lib/modules/2.6.35-22-generic/kernel/sound
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
checking for usb_endpoint_dir_in and related functions... yes
checking for usb_endpoint_xfer_control... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for fmode_t... yes
checking for hrtimer_get_expires... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
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
checking for driver version... 1.0.23
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
checking for valid v1 in linux/usb/audio.h... no
Creating <linux/usb/audio.h>...
checking for kernel linux/usb/ch9.h... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for bool... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
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
checking for cards to compile driver for... all
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
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
(cd include/sound && ln -s ../../alsa-kernel/include/*.h .)
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
#@for d in include acore i2c drivers isa synth pci aoa soc usb pcmcia misc; do if ! make -C $d prepare; then exit 1; fi; done
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hrtimer.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hrtimer.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.inc:1,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.inc:1,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/sgbuf.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm_native.c:2:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2099: note: this is the location of the previous definition
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/pcm_native.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [compile] Error 2
```

I could use some help here; with the package partially installed I have no sound at all.  I have kernel headers and every related -dev package I can think of installed.  I'm running 64-bit; could that be an issue?

---

### Post by CarpKing on 2010-10-12
Bump.  Would this thread be better suited to the Compiling subforum since the error comes from make?

---

### Post by 542 on 2010-10-12
Hi, sorry no help. But I also have exactly the same error.

To at least get your sound back: apt-get remove the linuxant package and then reinstall the linux-image package which if I understand correctly reinstalls the alsa modules. That worked for me.

---

### Post by CarpKing on 2010-10-13
Good to know.  I might give that a try.  Interestingly I get the same error when I try to use the "compile" option on the ALSA-upgrade script (I had run that script before installing Linuxant on 10.04 and was hoping it would help things now).  Guess I'd better post a reply to that thread.

---

