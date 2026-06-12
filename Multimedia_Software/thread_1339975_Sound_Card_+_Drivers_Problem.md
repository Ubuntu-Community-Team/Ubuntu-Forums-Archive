---
title: "Sound Card + Drivers Problem"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Pikachuu on 2009-11-28
I just installed Ubuntu yesterday and there's no sound. I followed this link: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and got up to finding the Sound Card part: I had a Realtek card, so I scrolled to the bottom and downloaded and tried to install the drivers. I followed the Readme instructions and it still didn't work. Strange things happened at Step 3 though.

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. ./snddevices

I got to step 3a via:

```
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;$ ls
eGalaxTouch32  realtek-linux-audiopack-5.04  ubuntupocketguide-v1-1.pdf
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;$ cd realtek-linux-audiopack.5.04
bash: cd: realtek-linux-audiopack.5.04: No such file or directory
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;$ cd realtek-linux-audiopack-5.04
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04$ ls
alsa-driver-rt20080527-5.04          alsa-utils-1.0.16.tar.bz2  test.wav.bz2
alsa-driver-rt20080527-5.04.tar.bz2  install                    version
alsa-lib-1.0.16.tar.bz2              Readme.txt
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04$ cd alsa-driv
er-rt20080527-5.04
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-r
t20080527-5.04$ 

```

Then when I type in the command in 3b: 

```
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-r
t20080527-5.04$ sudo ./configure
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
checking for current directory... /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.31-15-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.31-15-generic
checking for GCC version... ./configure: eval: line 4853: syntax error near unexpected token `)'
./configure: eval: line 4853: `my_compiler_version=4.4.1-4ubuntu8)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.1-4ubuntu8) 4.4.1

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
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
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
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel linux/seq_file.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.31-15-generic/kernel/sound
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
checking for driver extra-version... 
checking for driver version... 1.0.16
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
checking for new IRQ handler... no
checking for gfp_t... no
checking for PnP suspend/resume... no
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... no
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
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
```

I used sudo to be safe. For 3c: 

```
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-r
t20080527-5.04$ sudo make
make dep
make[1]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/ioctl32'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/ioctl32'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/oss'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/oss'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/seq'
make[4]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/seq/oss'
make[4]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/seq/oss'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/seq'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/i2c'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/i2c/l3'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/i2c/l3'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/i2c/other'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/i2c/other'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/i2c'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/mpu401'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/mpu401'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/opl3'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/opl3'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/opl4'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/opl4'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/pcsp'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/pcsp'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/vx'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers/vx'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/drivers'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/ad1816a'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/ad1816a'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/ad1848'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/ad1848'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/cs423x'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/cs423x'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/es1688'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/es1688'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/gus'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/gus'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/msnd'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/msnd'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/opti9xx'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/opti9xx'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/sb'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/sb'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/wavefront'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa/wavefront'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/isa'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/synth'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/synth/emux'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/synth/emux'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/synth'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ac97'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ac97'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ali5451'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ali5451'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/asihpi'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/asihpi'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/au88x0'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/au88x0'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/aw2'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/aw2'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ca0106'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ca0106'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/cs46xx'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/cs46xx'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/cs5535audio'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/cs5535audio'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/echoaudio'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/echoaudio'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/emu10k1'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/emu10k1'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/hda'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/hda'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ice1712'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ice1712'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/korg1212'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/korg1212'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/mixart'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/mixart'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/nm256'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/nm256'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/oxygen'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/oxygen'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/pcxhr'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/pcxhr'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/pdplus'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/pdplus'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/riptide'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/riptide'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/rme9652'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/rme9652'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/trident'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/trident'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/vx222'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/vx222'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ymfpci'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci/ymfpci'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pci'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/codecs'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/codecs'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/core'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/core'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/fabrics'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/fabrics'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/soundbus'
make[4]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa/soundbus'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/aoa'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/at91'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/at91'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/codecs'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/codecs'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/davinci'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/davinci'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/fsl'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/fsl'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/omap'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/omap'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/pxa'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/pxa'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/s3c24xx'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/s3c24xx'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/sh'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc/sh'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/soc'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/usb'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/usb/caiaq'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/usb/caiaq'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/usb/usx2y'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/usb/usx2y'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/usb'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pcmcia'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pcmcia/vx'
make[3]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pcmcia/vx'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/pcmcia'
make[2]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/misc'
make[2]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/misc'
make[1]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04'
make -C /lib/modules/2.6.31-15-generic/build SUBDIRS=/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-15-generic'
  CC [M]  /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/hwdep.o
In file included from /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/hwdep.c:1:
/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:823: error: static declaration of ‘jiffies_to_msecs’ follows non-static declaration
include/linux/jiffies.h:296: note: previous declaration of ‘jiffies_to_msecs’ was here
/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:842: error: static declaration of ‘msecs_to_jiffies’ follows non-static declaration
include/linux/jiffies.h:298: note: previous declaration of ‘msecs_to_jiffies’ was here
In file included from /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:940,
                 from /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/hwdep.c:1:
include/linux/pci.h:707: error: expected identifier or ‘(’ before numeric constant
In file included from /usr/src/linux-headers-2.6.31-15-generic/arch/x86/include/asm/pci.h:4,
                 from include/linux/pci.h:1112,
                 from /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:940,
                 from /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/hwdep.c:1:
include/linux/mm.h:267: error: conflicting types for ‘snd_compat_vmalloc_to_page’
/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:744: note: previous declaration of ‘snd_compat_vmalloc_to_page’ was here
In file included from /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/hwdep.c:1:
/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:1182: error: too many arguments to function ‘pci_save_state’
/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
[B]/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/adriver.h:1186: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore/hwdep.o] Error 1
make[2]: *** [/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore] Error 2
make[1]: *** [_module_/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-15-generic'
make: *** [compile] Error 2[/B]

```

Bolded part says error, but I don't know what error it could be.

I go straight to 3d:

```
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-r
t20080527-5.04$ sudo make install
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
find /lib/modules/2.6.31-15-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.31-15-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.31-15-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.31-15-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore'
mkdir -p /lib/modules/2.6.31-15-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.31-15-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/pikachu/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-rt20080527-5.04/acore'
make: *** [install-modules] Error 1

```

Hello trainwreck.

Then finally 3e: 

```
pikachu@pikachu-laptop:~/&#12487;&#12473;&#12463;&#12488;&#12483;&#12503;/realtek-linux-audiopack-5.04/alsa-driver-r
t20080527-5.04$ sudo ./snddevices
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
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.

```

Which appears to look fine...

I think I may have messed up my system slightly, since I can no longer use the command in the link at the top of the post to get the model of my sound card.

Any help would be gladly appreciated. :D

---

### Post by Pikachuu on 2009-12-01
bump.

Does anyone have an inkling on what's wrong?

Please don't be intimidated by the Japanese characters, it just says desktop. >_<

---

### Post by Ulysses361 on 2009-12-02
Please execute step 1, then reboot and send us output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Please also specify the exact model and make of pc that you are using.

---

### Post by Pikachuu on 2009-12-03
Step 1 worked :o

Something must have gone wrong with my Ubuntu installation, that's why it wouldn't work. >_< I couldn't even run the alsa version command at the beginning of the installation guide, but now I can.

Don't think I still need to add more output.

Sorry for the trouble over such a minor problem. >_<

EDIT: Streaming through Firefox works, but playback through players doesn't. I've reinstalled the mp3 codecs multiple times and they won't play either. Should I make another thread or continue here?

EDIT2: More toying around reveals that my sound and the default mixer that opens when Ubuntu boots aren't linked. I muted in that mixer, but the sound from Youtube/Imeem/Flash Games keeps playing.

EDIT3: I'm using a HP Touchsmart tx2 laptop.

Step 3: [http://pastebin.ca/1700235](http://pastebin.ca/1700235)

Step 4:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  flashplugin-nonfree-extrasound gnome-alsamixer libgconfmm-2.6-1c2{a} 
  libglademm-2.4-1c2a{a} padevchooser{a} paman paprefs{a} pavucontrol{a} 
  pavumeter{a} pulseaudio-module-zeroconf{a} 
The following packages will be REMOVED:
  libamrnb3{u} libamrwb3{u} 
0 packages upgraded, 10 newly installed, 2 to remove and 0 not upgraded.
Need to get 508kB of archives. After unpacking 2,929kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://sg.archive.ubuntu.com karmic/multiverse flashplugin-nonfree-extrasound 0.0.svn2431-3 [8,160B]
Get:2 http://sg.archive.ubuntu.com karmic/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-2 [53.7kB]
Get:3 http://sg.archive.ubuntu.com karmic/main libgconfmm-2.6-1c2 2.24.0-2 [31.4kB]
Get:4 http://sg.archive.ubuntu.com karmic/main libglademm-2.4-1c2a 2.6.7-2 [21.7kB]
Get:5 http://sg.archive.ubuntu.com karmic/universe pavumeter 0.9.3-1ubuntu1 [29.2kB]
Get:6 http://sg.archive.ubuntu.com karmic/universe pavucontrol 0.9.8+git20090701-0ubuntu2 [120kB]
Get:7 http://sg.archive.ubuntu.com karmic/universe paman 0.9.4-1ubuntu2 [92.2kB]
Get:8 http://sg.archive.ubuntu.com karmic/main pulseaudio-module-zeroconf 1:0.9.19-0ubuntu4 [20.2kB]
Get:9 http://sg.archive.ubuntu.com karmic/universe paprefs 0.9.8+git20090825-0ubuntu2 [111kB]
Get:10 http://sg.archive.ubuntu.com karmic/universe padevchooser 0.9.3-2ubuntu4 [20.2kB]
Fetched 508kB in 11s (45.3kB/s)                                                 
(Reading database ... 175329 files and directories currently installed.)
Removing libamrnb3 ...
Removing libamrwb3 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package flashplugin-nonfree-extrasound.
(Reading database ... 175310 files and directories currently installed.)
Unpacking flashplugin-nonfree-extrasound (from .../flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb) ...
Selecting previously deselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb) ...
Selecting previously deselected package libgconfmm-2.6-1c2.
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.24.0-2_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2_i386.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.8+git20090701-0ubuntu2_i386.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_1%3a0.9.19-0ubuntu4_i386.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.8+git20090825-0ubuntu2_i386.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Setting up flashplugin-nonfree-extrasound (0.0.svn2431-3) ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2) ...

Setting up libgconfmm-2.6-1c2 (2.24.0-2) ...

Setting up libglademm-2.4-1c2a (2.6.7-2) ...

Setting up pavumeter (0.9.3-1ubuntu1) ...

Setting up pavucontrol (0.9.8+git20090701-0ubuntu2) ...

Setting up paman (0.9.4-1ubuntu2) ...

Setting up pulseaudio-module-zeroconf (1:0.9.19-0ubuntu4) ...
Setting up paprefs (0.9.8+git20090825-0ubuntu2) ...

Setting up padevchooser (0.9.3-2ubuntu4) ...

Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
  *-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:d2400000-d2403fff
total 0
crw-rw----+  1 root audio 116, 33 2009-12-03 21:56 timer
crw-rw----+  1 root audio 116,  1 2009-12-03 21:56 seq
crw-rw----+  1 root audio 116, 24 2009-12-03 21:56 pcmC0D0c
crw-rw----+  1 root audio 116,  4 2009-12-03 21:56 hwC0D0
crw-rw----+  1 root audio 116,  5 2009-12-03 21:56 hwC0D1
crw-rw----+  1 root audio 116,  0 2009-12-03 21:56 controlC0
drwxr-xr-x   2 root root       60 2009-12-03 21:56 by-path
drwxr-xr-x   3 root root      240 2009-12-03 21:56 .
crw-rw----+  1 root audio 116, 22 2009-12-03 21:56 pcmC0D6p
crw-rw----+  1 root audio 116, 30 2009-12-03 21:56 pcmC0D6c
crw-rw----+  1 root audio 116, 16 2009-12-03 22:02 pcmC0D0p
drwxr-xr-x  18 root root     4040 2009-12-03 23:23 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux pikachu-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA ATI SB at 0xd2400000 irq 16

Audio devices:
0: ALC268 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC268
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control [1022:1304]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
08:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
/usr/sbin/alsactl
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd   1222 F.... slmodemd
                     pikachu    4598 F.... firefox
/dev/snd/pcmC0D0p:   pikachu    4598 F...m firefox
/dev/snd/pcmC0D6c:   Slmodemd   1222 F...m slmodemd
/dev/snd/pcmC0D6p:   Slmodemd   1222 F...m slmodemd
/dev/snd/timer:      pikachu    4598 f.... firefox
sl-modem-daemon: /usr/sbin/slmodemd
Status of SmartLink modem daemon: slmodemd is running.
snd_hda_codec_si3054     4828  1 
snd_hda_codec_realtek   200576  1 
snd_hda_intel          26560  6 
snd_hda_codec          78300  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
snd_pcm_oss            37472  0 
snd_mixer_oss          16188  1 snd_pcm_oss
snd_pcm                75168  7 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29216  0 
snd_seq_midi            6656  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21540  3 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60164  23 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9124  2 snd_hda_intel,snd_pcm

```EDIT4: I went down to step 10, and my user is not in the pulse-rt Group... Could be a root of the problem.

EDIT5: Got the chip names.
Codec: Realtek ALC268
Codec: Motorola Si3054

---

### Post by Ulysses361 on 2009-12-03
Your output from step 4 shows the issue your pc is having:

/dev/snd/controlC0:  Slmodemd   1222 F.... slmodemd

Your Si3054 Modem is hogging the /dev/snd devices, which is preventing your soundcard from working correctly.

Please try this solution:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/87927](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/87927)

which mentions this bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500/comments/40](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500/comments/40)

So you need to disable the Si3054 Modem (56k modem) via System/Administration/Hardware drivers

---

### Post by Pikachuu on 2009-12-04
Yeah, the volume control works now. Thanks. :D I can also hear the log-in sounds. The media players still refuse to play anything though.

I'll go upgrade the OS to 64-bit (I forgot my laptop could support it) and see if the problem still persists.

EDIT: The instant I closed Firefox the sound started to play... Well, off to install 64-bit Ubuntu.

---

### Post by Pikachuu on 2009-12-05
Posting to say that my sound is working all fine now.

Thank you very much Ulysses! :3

---

