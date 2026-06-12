---
title: "Problem with installing audio driver"
date: 2009-03-27
forum: Multimedia Software
---

### Post by SHENGTON on 2009-03-27
Hello guys, good evening. :)

I got here an ASUS P5PE-VM which has a Linux Drivers. My motherboard has only 3 drivers for Linux (audio, graphics, and network). For now I want to solve my problem regarding my audio driver. I'll post my other problems with my graphic and network drivers after this. 

I put the CD of my ASUS and browse to the audio driver folder and the file name of the driver is "**alsa-driver-0.9.ladi.tgz**". I read the "README.txt" and in the installation part it's said that there are three basic commands needed to build the AC97 ALSA driver are summarize here.

```
./configure --with-cards=intel8x0
make install
./snddevices
```

Here's the result when I executed the "**./configure --with-cards=intelx0**" command:
```
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/shengton/Desktop/audio
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.27-11-generic/build
checking for kernel version... 0.0.0
checking for kenrel linux/pm.h... "yes"
checking for kenrel linux/spinlock.h... "yes"
checking for kenrel linux/irq.h... "yes"
checking for kenrel linux/threads.h... "yes"
checking for kenrel linux/rwsem.h... "yes"
checking for kenrel linux/gameport.h... "yes"
checking for kenrel linux/devfs_fs_kernel.h... "no"
checking for kenrel linux/workqueue.h... "yes"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... i586
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for ISA PnP support... yes
checking for old kill_fasync... "no"
checking for dma_addr_t... "yes"
checking for MUTEX macros... "no"
checking for vmalloc_to_page... "no"
checking for driver version... 0.9.1
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for USB support... "no"
checking for USB module support... "yes"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "yes"
checking for PC9800 support in kernel... "no"
checking for which soundcards to compile driver for... intel8x0
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
```

Here's the result when I executed the "**make install**" command:
```
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:47:1: warning: "PMD_SHIFT" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:19:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:48:1: warning: "PTRS_PER_PMD" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:20:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:60:1: warning: "pmd_ERROR" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:33:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:63:1: warning: "pud_ERROR" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopud.h:29:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h: In function &#8216;native_pmd_clear&#8217;:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:114: warning: implicit declaration of function &#8216;native_make_pmd&#8217;
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:114: error: incompatible type for argument 2 of &#8216;native_set_pmd&#8217;
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h: In function &#8216;native_pud_clear&#8217;:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:124: warning: implicit declaration of function &#8216;native_make_pud&#8217;
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:124: error: incompatible type for argument 2 of &#8216;native_set_pud&#8217;
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:141:1: warning: "PMD_SIZE" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:21:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:142:1: warning: "PMD_MASK" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:22:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:143:1: warning: "PUD_SIZE" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopud.h:17:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:144:1: warning: "PUD_MASK" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopud.h:18:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:149:1: warning: "MAXMEM" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:44,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/page_32.h:93:1: warning: this is the location of the previous definition
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h: At top level:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:159: error: redefinition of &#8216;pgd_bad&#8217;
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopud.h:26: error: previous definition of &#8216;pgd_bad&#8217; was here
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:164: error: redefinition of &#8216;pud_bad&#8217;
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:30: error: previous definition of &#8216;pud_bad&#8217; was here
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:195:1: warning: "pgd_page_vaddr" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopud.h:47:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:197:1: warning: "pgd_page" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopud.h:46:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:204:1: warning: "pud_page_vaddr" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:52:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pgtable.h:364,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/mm.h:39,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm/pgtable_64.h:206:1: warning: "pud_page" redefined
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/page.h:131,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/pda.h:8,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/current.h:19,
                 from /lib/modules/2.6.27-11-generic/build/include/asm/processor.h:15,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/list.h:6,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/module.h:9,
                 from /home/shengton/Desktop/audio/include/adriver.h:49,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/asm-generic/pgtable-nopmd.h:51:1: warning: this is the location of the previous definition
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h: In function &#8216;virt_to_head_page&#8217;:
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h:302: warning: implicit declaration of function &#8216;__pfn_to_page&#8217;
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h:302: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h:302: warning: initialization makes pointer from integer without a cast
In file included from /lib/modules/2.6.27-11-generic/build/include/asm/pci.h:4,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/pci.h:989,
                 from /home/shengton/Desktop/audio/include/linux/isapnp.h:130,
                 from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h: In function &#8216;lowmem_page_address&#8217;:
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h:591: warning: implicit declaration of function &#8216;__page_to_pfn&#8217;
/lib/modules/2.6.27-11-generic/build/include/linux/mm.h:591: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
In file included from /home/shengton/Desktop/audio/include/adriver.h:124,
                 from memalloc.c:11:
/home/shengton/Desktop/audio/include/linux/isapnp.h: At top level:
/home/shengton/Desktop/audio/include/linux/isapnp.h:334: warning: &#8216;struct isapnp_card_id&#8217; declared inside parameter list
/home/shengton/Desktop/audio/include/linux/isapnp.h:334: warning: its scope is only this definition or declaration, which is probably not what you want
In file included from /lib/modules/2.6.27-11-generic/build/include/linux/ktime.h:25,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/timer.h:5,
                 from /lib/modules/2.6.27-11-generic/build/include/linux/workqueue.h:8,
                 from /home/shengton/Desktop/audio/include/adriver.h:282,
                 from memalloc.c:11:
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:39:3: error: #error Invalid value of HZ.
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
/lib/modules/2.6.27-11-generic/build/include/linux/jiffies.h:247:31: error: division by zero in #if
In file included from memalloc.c:28:
../alsa-kernel/core/memalloc.c:30:27: error: asm/semaphore.h: No such file or directory
In file included from memalloc.c:28:
../alsa-kernel/core/memalloc.c: In function &#8216;mark_pages&#8217;:
../alsa-kernel/core/memalloc.c:336: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
../alsa-kernel/core/memalloc.c:336: warning: initialization makes pointer from integer without a cast
../alsa-kernel/core/memalloc.c: In function &#8216;unmark_pages&#8217;:
../alsa-kernel/core/memalloc.c:345: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
../alsa-kernel/core/memalloc.c:345: warning: initialization makes pointer from integer without a cast
../alsa-kernel/core/memalloc.c: In function &#8216;snd_malloc_isa_pages&#8217;:
../alsa-kernel/core/memalloc.c:438: warning: implicit declaration of function &#8216;isa_virt_to_bus&#8217;
../alsa-kernel/core/memalloc.c: In function &#8216;snd_mem_init&#8217;:
../alsa-kernel/core/memalloc.c:737: error: &#8216;snd_mem_proc_read&#8217; undeclared (first use in this function)
make[1]: *** [memalloc.o] Error 1
make[1]: Leaving directory `/home/shengton/Desktop/audio/acore'
make: *** [compile] Error 1

```

Here's the result when I executed the "**./snddevices**" command:
```
rm: cannot remove `/dev/mixer': Permission denied
rm: cannot remove `/dev/mixer0': Permission denied
rm: cannot remove `/dev/mixer1': Permission denied
rm: cannot remove `/dev/mixer2': Permission denied
rm: cannot remove `/dev/mixer3': Permission denied
Creating /dev/mixer?...mknod: `/dev/mixer0': File exists
chown: changing ownership of `/dev/mixer0': Operation not permitted
mknod: `/dev/mixer1': File exists
chown: changing ownership of `/dev/mixer1': Operation not permitted
mknod: `/dev/mixer2': File exists
chown: changing ownership of `/dev/mixer2': Operation not permitted
mknod: `/dev/mixer3': File exists
chown: changing ownership of `/dev/mixer3': Operation not permitted
 done
rm: cannot remove `/dev/sequencer': Permission denied
Creating /dev/sequencer...mknod: `/dev/sequencer': File exists
chown: changing ownership of `/dev/sequencer': Operation not permitted
 done
rm: cannot remove `/dev/midi': Permission denied
Creating /dev/midi?...mknod: `/dev/midi0': Permission denied
chown: cannot access `/dev/midi0': No such file or directory
mknod: `/dev/midi1': Permission denied
chown: cannot access `/dev/midi1': No such file or directory
mknod: `/dev/midi2': Permission denied
chown: cannot access `/dev/midi2': No such file or directory
mknod: `/dev/midi3': Permission denied
chown: cannot access `/dev/midi3': No such file or directory
 done
rm: cannot remove `/dev/dsp': Permission denied
rm: cannot remove `/dev/dsp0': Permission denied
rm: cannot remove `/dev/dsp1': Permission denied
rm: cannot remove `/dev/dsp2': Permission denied
rm: cannot remove `/dev/dsp3': Permission denied
Creating /dev/dsp?...mknod: `/dev/dsp0': File exists
chown: changing ownership of `/dev/dsp0': Operation not permitted
mknod: `/dev/dsp1': File exists
chown: changing ownership of `/dev/dsp1': Operation not permitted
mknod: `/dev/dsp2': File exists
chown: changing ownership of `/dev/dsp2': Operation not permitted
mknod: `/dev/dsp3': File exists
chown: changing ownership of `/dev/dsp3': Operation not permitted
 done
rm: cannot remove `/dev/audio': Permission denied
rm: cannot remove `/dev/audio0': Permission denied
rm: cannot remove `/dev/audio1': Permission denied
rm: cannot remove `/dev/audio2': Permission denied
rm: cannot remove `/dev/audio3': Permission denied
Creating /dev/audio?...mknod: `/dev/audio0': File exists
chown: changing ownership of `/dev/audio0': Operation not permitted
mknod: `/dev/audio1': File exists
chown: changing ownership of `/dev/audio1': Operation not permitted
mknod: `/dev/audio2': File exists
chown: changing ownership of `/dev/audio2': Operation not permitted
mknod: `/dev/audio3': File exists
chown: changing ownership of `/dev/audio3': Operation not permitted
 done
rm: cannot remove `/dev/sndstat': Permission denied
Creating /dev/sndstat...mknod: `/dev/sndstat': File exists
chown: changing ownership of `/dev/sndstat': Operation not permitted
 done
rm: cannot remove `/dev/music': Permission denied
Creating /dev/music...mknod: `/dev/music': File exists
chown: changing ownership of `/dev/music': Operation not permitted
 done
rm: cannot remove `/dev/dmmidi0': Permission denied
rm: cannot remove `/dev/dmmidi1': Permission denied
rm: cannot remove `/dev/dmmidi2': Permission denied
rm: cannot remove `/dev/dmmidi3': Permission denied
Creating /dev/dmmidi?...mknod: `/dev/dmmidi0': File exists
chown: changing ownership of `/dev/dmmidi0': Operation not permitted
mknod: `/dev/dmmidi1': File exists
chown: changing ownership of `/dev/dmmidi1': Operation not permitted
mknod: `/dev/dmmidi2': File exists
chown: changing ownership of `/dev/dmmidi2': Operation not permitted
mknod: `/dev/dmmidi3': File exists
chown: changing ownership of `/dev/dmmidi3': Operation not permitted
 done
rm: cannot remove `/dev/dmfm0': Permission denied
rm: cannot remove `/dev/dmfm1': Permission denied
rm: cannot remove `/dev/dmfm2': Permission denied
rm: cannot remove `/dev/dmfm3': Permission denied
Creating /dev/dmfm?...mknod: `/dev/dmfm0': File exists
chown: changing ownership of `/dev/dmfm0': Operation not permitted
mknod: `/dev/dmfm1': File exists
chown: changing ownership of `/dev/dmfm1': Operation not permitted
mknod: `/dev/dmfm2': File exists
chown: changing ownership of `/dev/dmfm2': Operation not permitted
mknod: `/dev/dmfm3': File exists
chown: changing ownership of `/dev/dmfm3': Operation not permitted
 done
rm: cannot remove `/dev/amixer0': Permission denied
rm: cannot remove `/dev/amixer1': Permission denied
rm: cannot remove `/dev/amixer2': Permission denied
rm: cannot remove `/dev/amixer3': Permission denied
Creating /dev/amixer?...mknod: `/dev/amixer0': File exists
chown: changing ownership of `/dev/amixer0': Operation not permitted
mknod: `/dev/amixer1': File exists
chown: changing ownership of `/dev/amixer1': Operation not permitted
mknod: `/dev/amixer2': File exists
chown: changing ownership of `/dev/amixer2': Operation not permitted
mknod: `/dev/amixer3': File exists
chown: changing ownership of `/dev/amixer3': Operation not permitted
 done
rm: cannot remove `/dev/adsp': Permission denied
rm: cannot remove `/dev/adsp0': Permission denied
rm: cannot remove `/dev/adsp1': Permission denied
rm: cannot remove `/dev/adsp2': Permission denied
rm: cannot remove `/dev/adsp3': Permission denied
Creating /dev/adsp?...mknod: `/dev/adsp0': File exists
chown: changing ownership of `/dev/adsp0': Operation not permitted
mknod: `/dev/adsp1': File exists
chown: changing ownership of `/dev/adsp1': Operation not permitted
mknod: `/dev/adsp2': File exists
chown: changing ownership of `/dev/adsp2': Operation not permitted
mknod: `/dev/adsp3': File exists
chown: changing ownership of `/dev/adsp3': Operation not permitted
 done
rm: cannot remove `/dev/amidi': Permission denied
rm: cannot remove `/dev/amidi0': Permission denied
rm: cannot remove `/dev/amidi1': Permission denied
rm: cannot remove `/dev/amidi2': Permission denied
rm: cannot remove `/dev/amidi3': Permission denied
Creating /dev/amidi?...mknod: `/dev/amidi0': File exists
chown: changing ownership of `/dev/amidi0': Operation not permitted
mknod: `/dev/amidi1': File exists
chown: changing ownership of `/dev/amidi1': Operation not permitted
mknod: `/dev/amidi2': File exists
chown: changing ownership of `/dev/amidi2': Operation not permitted
mknod: `/dev/amidi3': File exists
chown: changing ownership of `/dev/amidi3': Operation not permitted
 done
rm: cannot remove `/dev/admmidi0': Permission denied
rm: cannot remove `/dev/admmidi1': Permission denied
rm: cannot remove `/dev/admmidi2': Permission denied
rm: cannot remove `/dev/admmidi3': Permission denied
Creating /dev/admmidi?...mknod: `/dev/admmidi0': File exists
chown: changing ownership of `/dev/admmidi0': Operation not permitted
mknod: `/dev/admmidi1': File exists
chown: changing ownership of `/dev/admmidi1': Operation not permitted
mknod: `/dev/admmidi2': File exists
chown: changing ownership of `/dev/admmidi2': Operation not permitted
mknod: `/dev/admmidi3': File exists
chown: changing ownership of `/dev/admmidi3': Operation not permitted
 done
ln: cannot remove `/dev/mixer': Permission denied
ln: cannot remove `/dev/midi': Permission denied
ln: cannot remove `/dev/dsp': Permission denied
ln: cannot remove `/dev/audio': Permission denied
ln: cannot remove `/dev/sequencer2': Permission denied
ln: cannot remove `/dev/adsp': Permission denied
ln: cannot remove `/dev/amidi': Permission denied
mv: cannot move `/dev/sndstat' to `/dev/1sndstat': Permission denied
rm: cannot remove `/dev/snd': Permission denied
rm: cannot remove `/dev/sndstat': Permission denied
mv: cannot stat `/dev/1sndstat': No such file or directory
rm: cannot remove `/dev/snd/controlC0': Permission denied
rm: cannot remove `/dev/snd/controlC1': Permission denied
rm: cannot remove `/dev/snd/controlC2': Permission denied
rm: cannot remove `/dev/snd/controlC3': Permission denied
rm: cannot remove `/dev/snd/hwC0D0': Permission denied
rm: cannot remove `/dev/snd/hwC0D1': Permission denied
rm: cannot remove `/dev/snd/hwC0D2': Permission denied
rm: cannot remove `/dev/snd/hwC0D3': Permission denied
rm: cannot remove `/dev/snd/hwC1D0': Permission denied
rm: cannot remove `/dev/snd/hwC1D1': Permission denied
rm: cannot remove `/dev/snd/hwC1D2': Permission denied
rm: cannot remove `/dev/snd/hwC1D3': Permission denied
rm: cannot remove `/dev/snd/hwC2D0': Permission denied
rm: cannot remove `/dev/snd/hwC2D1': Permission denied
rm: cannot remove `/dev/snd/hwC2D2': Permission denied
rm: cannot remove `/dev/snd/hwC2D3': Permission denied
rm: cannot remove `/dev/snd/hwC3D0': Permission denied
rm: cannot remove `/dev/snd/hwC3D1': Permission denied
rm: cannot remove `/dev/snd/hwC3D2': Permission denied
rm: cannot remove `/dev/snd/hwC3D3': Permission denied
rm: cannot remove `/dev/snd/midiC0D0': Permission denied
rm: cannot remove `/dev/snd/midiC0D1': Permission denied
rm: cannot remove `/dev/snd/midiC0D2': Permission denied
rm: cannot remove `/dev/snd/midiC0D3': Permission denied
rm: cannot remove `/dev/snd/midiC0D4': Permission denied
rm: cannot remove `/dev/snd/midiC0D5': Permission denied
rm: cannot remove `/dev/snd/midiC0D6': Permission denied
rm: cannot remove `/dev/snd/midiC0D7': Permission denied
rm: cannot remove `/dev/snd/midiC1D0': Permission denied
rm: cannot remove `/dev/snd/midiC1D1': Permission denied
rm: cannot remove `/dev/snd/midiC1D2': Permission denied
rm: cannot remove `/dev/snd/midiC1D3': Permission denied
rm: cannot remove `/dev/snd/midiC1D4': Permission denied
rm: cannot remove `/dev/snd/midiC1D5': Permission denied
rm: cannot remove `/dev/snd/midiC1D6': Permission denied
rm: cannot remove `/dev/snd/midiC1D7': Permission denied
rm: cannot remove `/dev/snd/midiC2D0': Permission denied
rm: cannot remove `/dev/snd/midiC2D1': Permission denied
rm: cannot remove `/dev/snd/midiC2D2': Permission denied
rm: cannot remove `/dev/snd/midiC2D3': Permission denied
rm: cannot remove `/dev/snd/midiC2D4': Permission denied
rm: cannot remove `/dev/snd/midiC2D5': Permission denied
rm: cannot remove `/dev/snd/midiC2D6': Permission denied
rm: cannot remove `/dev/snd/midiC2D7': Permission denied
rm: cannot remove `/dev/snd/midiC3D0': Permission denied
rm: cannot remove `/dev/snd/midiC3D1': Permission denied
rm: cannot remove `/dev/snd/midiC3D2': Permission denied
rm: cannot remove `/dev/snd/midiC3D3': Permission denied
rm: cannot remove `/dev/snd/midiC3D4': Permission denied
rm: cannot remove `/dev/snd/midiC3D5': Permission denied
rm: cannot remove `/dev/snd/midiC3D6': Permission denied
rm: cannot remove `/dev/snd/midiC3D7': Permission denied
rm: cannot remove `/dev/snd/pcmC0D0c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D0p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D1c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D1p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D2c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D2p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D3c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D3p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D4c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D4p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D5c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D5p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D6c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D6p': Permission denied
rm: cannot remove `/dev/snd/pcmC0D7c': Permission denied
rm: cannot remove `/dev/snd/pcmC0D7p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D0c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D0p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D1c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D1p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D2c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D2p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D3c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D3p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D4c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D4p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D5c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D5p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D6c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D6p': Permission denied
rm: cannot remove `/dev/snd/pcmC1D7c': Permission denied
rm: cannot remove `/dev/snd/pcmC1D7p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D0c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D0p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D1c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D1p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D2c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D2p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D3c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D3p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D4c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D4p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D5c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D5p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D6c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D6p': Permission denied
rm: cannot remove `/dev/snd/pcmC2D7c': Permission denied
rm: cannot remove `/dev/snd/pcmC2D7p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D0c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D0p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D1c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D1p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D2c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D2p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D3c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D3p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D4c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D4p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D5c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D5p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D6c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D6p': Permission denied
rm: cannot remove `/dev/snd/pcmC3D7c': Permission denied
rm: cannot remove `/dev/snd/pcmC3D7p': Permission denied
rm: cannot remove `/dev/snd/seq': Permission denied
rm: cannot remove `/dev/snd/timer': Permission denied
rmdir: failed to remove `/dev/snd': Permission denied
ALSA dynamic sound device filesystem
ln: creating symbolic link `/dev/snd/dev': Permission denied
ALSA loader devices
rm: cannot remove `/dev/aloadC0': Permission denied
rm: cannot remove `/dev/aloadC1': Permission denied
rm: cannot remove `/dev/aloadC2': Permission denied
rm: cannot remove `/dev/aloadC3': Permission denied
rm: cannot remove `/dev/aloadSEQ': Permission denied
Creating /dev/aload?...mknod: `/dev/aloadC0': File exists
chown: changing ownership of `/dev/aloadC0': Operation not permitted
mknod: `/dev/aloadC1': File exists
chown: changing ownership of `/dev/aloadC1': Operation not permitted
mknod: `/dev/aloadC2': File exists
chown: changing ownership of `/dev/aloadC2': Operation not permitted
mknod: `/dev/aloadC3': File exists
chown: changing ownership of `/dev/aloadC3': Operation not permitted
 done
rm: cannot remove `/dev/aloadSEQ': Permission denied
Creating /dev/aloadSEQ...mknod: `/dev/aloadSEQ': File exists
chown: changing ownership of `/dev/aloadSEQ': Operation not permitted
 done

```

I know the installation is not successful since I see some errors like "no", "Permission denied", and "Operation not permitted". 

But what I don't know is, is/are the MARKS that indicates if the installation is succesful. Can you give me some MARKS if the installation is succesful or complete?

I don't know what I'm going to install seems it is looking for some libraries to complete the installation.

Hope someone will help me with this. Waiting for your  replies guys. :)

Take care and God bless. :)

---

### Post by SHENGTON on 2009-03-28
Anyone?

---

### Post by kruegger on 2009-03-28
Before your bolts and nuts get loosen ](*,), I suggest you forget about compiling... almost anything.
Your motherboard will function well with the drivers your distro has.
Among other things, your distro compiler has to be compatible with that of your motherboard manufacturer, which does not occur frecuently. 
To fix your issue, developers help is needed. And a good one.

Sorry if I'm not useful

---

### Post by SHENGTON on 2009-03-28
Hello kruegger, good evening. :)

So you mean the Linux Drivers that I have here is only compatible with one distro?

Take care and God bless. :)

---

