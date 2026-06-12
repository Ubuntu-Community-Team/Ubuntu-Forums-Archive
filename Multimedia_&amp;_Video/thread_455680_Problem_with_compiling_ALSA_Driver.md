---
title: "Problem with compiling ALSA Driver"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by bookwyrmy on 2007-05-26
I was following the directions on the Comprehensive Sound Problem Solutions Guide for compiling the ALSA Driver, but the module-assistant always stops at 49% and gives me this

```
 make[3]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'     
CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o                    
In file included from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     
/usr/src/modules/alsa-driver/acore/memalloc.inc:1:26: error:               
linux/config.h: No such file or directory                                  
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,  
                 from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     
/usr/src/modules/alsa-driver/include/adriver.h:742: error: redefinition    
of &#8216;jiffies_to_msecs&#8217;                                                      
include/linux/jiffies.h:268: error: previous definition of                 
&#8216;jiffies_to_msecs&#8217; was here                                                
/usr/src/modules/alsa-driver/include/adriver.h:761: error: redefinition    
of &#8216;msecs_to_jiffies&#8217;                                                      
include/linux/jiffies.h:290: error: previous definition of      
&#8216;msecs_to_jiffies&#8217; was here                                                
In file included from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,  
                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:     
/usr/src/modules/alsa-driver/include/adriver.h: In function                
&#8216;snd_pci_orig_save_state&#8217;:                                                 
/usr/src/modules/alsa-driver/include/adriver.h:1099: error: too many       
arguments to function &#8216;pci_save_state&#8217;                                     
/usr/src/modules/alsa-driver/include/adriver.h: In function                
&#8216;snd_pci_orig_restore_state&#8217;:                                              
/usr/src/modules/alsa-driver/include/adriver.h:1103: error: too many       
arguments to function &#8216;pci_restore_state&#8217;  
make[6]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1       
make[5]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  
make[4]: *** [_module_/usr/src/modules/alsa-driver] Error 2                
make[3]: *** [modules] Error 2                                             
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'      
make[2]: *** [compile] Error 2                                             
make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  
make[1]: *** [build-stamp] Error 2                                         
make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  
make: *** [kdist_image] Error 2    
```

Without the module-assistant, I get this

```
sudo: ./configure: command not found
```

When I tried using drivers from the alsa-project, at sudo make I got this

```
make[1]: Entering directory `/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include  -I/usr/src/linux-headers-2.6.20-15-generic/include -I/usr/src/linux-headers-2.6.20-15-generic/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -Wdeclaration-after-statement -Wno-pointer-sign -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /usr/src/linux-headers-2.6.20-15-generic/include/linux/modversions.h   -DEXPORT_SYMTAB -c memalloc.c
cc1: error: /usr/src/linux-headers-2.6.20-15-generic/include/linux/modversions.h: No such file or directory
In file included from memalloc.c:1:
memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/asm/percpu.h:5,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/asm/processor.h:21,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:48,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/asm-generic/percpu.h:8: error: &#8216;CONFIG_NR_CPUS&#8217; undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/prefetch.h:14,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/list.h:8,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:48,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/processor.h:82: error: &#8216;CONFIG_X86_L1_CACHE_SHIFT&#8217; undeclared here (not in a function)
/usr/src/linux-headers-2.6.20-15-generic/include/asm/processor.h:82: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/module.h:15,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/device.h:20,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/module.h:15,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/device.h:20,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;jiffies_to_msecs&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:274: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:274: error: for each function it appears in.)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:280:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;jiffies_to_usecs&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:285: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:293:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;msecs_to_jiffies&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:298: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:306:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;usecs_to_jiffies&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:311: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;timespec_to_jiffies&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:330: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:336: error: &#8216;SHIFT_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;jiffies_to_timespec&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:349: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;timeval_to_jiffies&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:371: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:375: error: &#8216;SHIFT_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;jiffies_to_timeval&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:387: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;jiffies_to_clock_t&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:401: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;clock_t_to_jiffies&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:412: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h: In function &#8216;jiffies_64_to_clock_t&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:432: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/gfp.h:4,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/slab.h:14,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/percpu.h:5,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/rcupdate.h:41,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pid.h:4,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/sched.h:72,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/module.h:15,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/device.h:20,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mmzone.h: At top level:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mmzone.h:43: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mmzone.h:85: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mmzone.h:282: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pid.h:4,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/sched.h:72,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/module.h:15,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/device.h:20,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.20-15-generic/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/module.h:21,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/device.h:20,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/asm/pci.h:6,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:746,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mm.h: In function &#8216;lowmem_page_address&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mm.h:539: warning: implicit declaration of function &#8216;__page_to_pfn&#8217;
/usr/src/linux-headers-2.6.20-15-generic/include/linux/mm.h:539: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/asm/pci.h:41,
                 from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:746,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/io.h: In function &#8216;virt_to_phys&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/io.h:77: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-generic/include/asm/io.h: In function &#8216;phys_to_virt&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/io.h:95: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15-generic/include/linux/pci.h:746,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/pci.h: In function &#8216;pci_dac_dma_to_page&#8217;:
/usr/src/linux-headers-2.6.20-15-generic/include/asm/pci.h:72: warning: implicit declaration of function &#8216;__pfn_to_page&#8217;
/usr/src/linux-headers-2.6.20-15-generic/include/asm/pci.h:72: warning: return makes pointer from integer without a cast
In file included from memalloc.inc:13,
                 from memalloc.c:1:
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: At top level:
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:719: error: redefinition of &#8216;jiffies_to_msecs&#8217;
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
In file included from memalloc.inc:13,
                 from memalloc.c:1:
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:721:31: error: division by zero in #if
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: In function &#8216;jiffies_to_msecs&#8217;:
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:726: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: At top level:
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:738: error: redefinition of &#8216;msecs_to_jiffies&#8217;
/usr/src/linux-headers-2.6.20-15-generic/include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:742:31: error: division by zero in #if
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: In function &#8216;msecs_to_jiffies&#8217;:
/home/bookwyrmy/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:747: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
memalloc.c: In function &#8216;snd_malloc_pages&#8217;:
memalloc.c:268: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
memalloc.c:268: warning: passing argument 1 of &#8216;mark_pages&#8217; makes pointer from integer without a cast
memalloc.c: In function &#8216;snd_free_pages&#8217;:
memalloc.c:289: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
memalloc.c:289: warning: passing argument 1 of &#8216;unmark_pages&#8217; makes pointer from integer without a cast
memalloc.c: In function &#8216;snd_malloc_dev_pages&#8217;:
memalloc.c:315: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
memalloc.c:315: warning: passing argument 1 of &#8216;mark_pages&#8217; makes pointer from integer without a cast
memalloc.c: In function &#8216;snd_free_dev_pages&#8217;:
memalloc.c:332: error: &#8216;CONFIG_PAGE_OFFSET&#8217; undeclared (first use in this function)
memalloc.c:332: warning: passing argument 1 of &#8216;unmark_pages&#8217; makes pointer from integer without a cast
make[1]: *** [memalloc.o] Error 1

```

At this point, my soundcard is not detected, and I have no sound, please help.

---

### Post by lexarrow on 2007-05-27
go [here]("http://ubuntuforums.org/showthread.php?t=455147&highlight=dv2000") for a howto on the latest alsa drivers. Do all the steps there except downloading and installing the patch (it's just a fix for HP dv2000). 

note: if 2.6.20-15-generic doesn't work, compile them for 2.6.20.15 (it worked in my case)

---

