---
title: "no 5.1"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by Skat on 2006-02-21
hello, i have a sound blaster live! 24bit and in the ubuntu 5.10 i cannot make it sound through the whole surround.  only the two front speakers work.

can anybody help me?

---

### Post by Talikar on 2006-02-23
I'd just like to mention that I have the same problem.

Sound Blaster Live! 24bit, all speakers do work and are connected (I've tested through Beep player) I can play 2 speakers at a time (doesn't matter which) but I can't get full surround either.

I think I know the problem though. Not sure which app it was, but something mentioned that ALSA or whatever only allowed 2 channels? How do I set it higher than that?

It may have something to do somewhere else though; I can't really "install" the proper drivers as you can see below:
```
./configure --with-cards=ca0106 --with-sequencer=yes --with-kernel=/usr/
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.9rc4a
checking cross compile...
checking for directory with kernel source... /usr/
checking for directory with kernel build...
checking for kernel version... 2.6.11
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "no"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "no"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "yes"
checking for kernel linux/highmem.h... "no"
checking for kernel linux/workqueue.h... "yes"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for kernel linux/moduleparam.h... "yes"
checking for kernel linux/syscalls.h... "yes"
checking for kernel linux/firmware.h... "yes"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for input subsystem in kernel... unknown
checking for directory to store kernel modules... /lib/modules/2.6.11/misc
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... "no"
checking for processor type... "unknown"
checking for SMP... "no"
checking for Video device support in kernel... "no"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... no
checking for Kernel ISA-PnP support... "no"
checking for Kernel ISA-PnP module support... "no"
no
checking for strlcpy... "no"
checking for snprintf... "no"
checking for vsnprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for msleep... "no"
checking for tty->count is the atomic type... "no"
checking for io_remap_pfn_range... "no"
checking for new io_remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for driver version... 1.0.9rc4a
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for HPET support... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for new unlocked/compat_ioctl... "no"
checking for PC-Speaker hook... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard ca0106

```

That is a very weird error message, am I missing something here?

---

### Post by Talikar on 2006-02-28
Ok, now that it's been 4 days and I see there's still no answer, I'm happy to report that it's ok if you don't know the answer, there isn't one.

The ca0106 card drivers for ALSA doesn't support Surround with the SB Live! 24bit as of yet, since the drivers for the ca0106 are meant for a much simpler card, and are just the only ones that work with the 24bit live version (unfortunately). Hopefully ALSA becomes updated enough to support surround sound for SB live! 24bit some day soon.

Until then, living with 2 speaker sound isn't so bad.:)

---

