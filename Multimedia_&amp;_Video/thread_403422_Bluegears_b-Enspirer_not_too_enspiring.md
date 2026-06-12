---
title: "Bluegears b-Enspirer not too enspiring"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by Yfrwlf on 2007-04-07
Since Bluegears says they support Linux, and they provide Linux drivers, I bought the b-Enspirer sound card thinking it would work.  As it turns out, even though the drivers are open source since the source code is provided (the only way to get these drivers) I figured it would just work.  Come to find out, it doesn't.  It's not an option in the volume control settings, and doing```
sudo asoundconf list
```also didn't list it, only my on-board sound card.  So off I went to compile the source drivers provided from [http://www.bluegears.com/download_b-Enspirer.html]("http://www.bluegears.com/download_b-Enspirer.html")

At first I got this message: "error: C compiler cannot create executables".  After checking around I found out that I needed the package "build-essential" to be installed.  That was no problem, and after doing so it would configure without error.  The problem came during the compilation (make) when it would get many errors including stuff like this:```
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if

```and stuff like```
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/lib/modules/2.6.20-13-generic/build/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:

```and finally things like```
memalloc.c: In function ‘snd_free_pages’:
memalloc.c:290: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
memalloc.c:290: warning: passing argument 1 of ‘unmark_pages’ makes pointer from integer without a cast

```The readme was really helpful *ahem*not*ahem* and provided this vast array of information about the required dependencies for compilation:```
Compile driver :

cd alsa-driver-1.0.11
./configure --with-cards=cmi8788
make
make install
./snddevices

Compile lib :
cd alsa-lib-1.0.11
./configure
make
make install
```Compiling and installing the libraries worked, but the drivers did not.

Does anyone know why this driver wouldn't be in the mainline kernel?  I know open source doesn't mean free from restrictions which may be why, but just wondering if anyone knows.  If they are one of the few sound card companies supporting Linux you'd think they would get more attention.

Perhaps it's because it's crap.  Maybe the card is too new and they just aren't that interested in working on their Linux drivers.  But, again, come on ya'll, if they have them open sourced, you'd think the community would be all over them in support.  Anyone have any idea what is going on, if I'm doing something wrong, and have any experiences with this or any other Bluegear sound cards??

Because of this kind of dysfunctionality and lack of support, if it's not my fault or something simple I've missed, I'll definitely not recommend this card to anyone else on Linux.

---

### Post by Yfrwlf on 2007-04-10
It turns out that the compilation scripts in the Bluegears drivers for this card just suck, at least right now, they are very borked.  I would recommend a different brand or perhaps an older Bluegears card, though I haven't tried the older ones.  Just a warning to those considering this card.

---

### Post by b1k3r4ck on 2007-04-11
I am working on switching over to Ubuntu as my primary OS. Unfortunately I have an ATI x1800xt graphics card and a X-Fi sound card. 

I found the Bluegears sound card and noticed it had linux drivers so I dumped $109 on it and it's just as bad as my X-Fi. I can compile the driver but I get an error when I try to make. 

"make[1]: *** [memalloc.o] Error 1
make[1]: Leaving directory `/home/b1k3r4ck/bluegears/alsa-driver-1.0.11/acore'
make: *** [compile] Error 1"


I'm very disappointed in this card in windows and now linux. I'm probably stuck with an old Turtle Beach card until these guys (Creative and/or Bluegears) can put out a driver or make their stuff work.

---

### Post by Yfrwlf on 2007-04-14
> **b1k3r4ck said:**
> I am working on switching over to Ubuntu as my primary OS. Unfortunately I have an ATI x1800xt graphics card and a X-Fi sound card. 

I found the Bluegears sound card and noticed it had linux drivers so I dumped $109 on it and it's just as bad as my X-Fi. I can compile the driver but I get an error when I try to make. 

"make[1]: *** [memalloc.o] Error 1
make[1]: Leaving directory `/home/b1k3r4ck/bluegears/alsa-driver-1.0.11/acore'
make: *** [compile] Error 1"


I'm very disappointed in this card in windows and now linux. I'm probably stuck with an old Turtle Beach card until these guys (Creative and/or Bluegears) can put out a driver or make their stuff work.

That's the same problem everyone who has tried it has gotten that I've heard.  If you want, try [COLOR="Blue"][the Open Sound System driver]("http://www.opensound.com/linux.html")[/COLOR] and see if it does anything, it may be compatible.

Anyone know of any other sound cards with open source drivers?

---

### Post by Ateoto on 2007-08-10
I actually just bought two of these cards not too long ago. They both work great in Windows XP, but now that I installed Ubuntu 7.04 on my Media Box, I can't get the card to work. I've only been trying for about an hour or so, but I sent a message off to Bgears support. I got a reply back in minutes saying that they had sent off my message to R&D who specializes in Linux. I was actually impressed with how fast the reply came back. But Anyway I'll  post here what I sent to them. I'm trying a few things now, and I'll repost when I get it working:

./configure works fine, make fails. The lib that comes in the bGears driver compiles and installs just fine, but here is the output from the make command.

make[1]: Entering directory `/home/matt/Desktop/alsa-driver-1.0.11/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/matt/Desktop/alsa-driver-1.0.11/include  -I/lib/modules/2.6.20-16-generic/build/include -I/lib/modules/2.6.20-16-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -Wdeclaration-after-statement -Wno-pointer-sign -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h   -DEXPORT_SYMTAB -c memalloc.c
cc1: error: /lib/modules/2.6.20-16-generic/build/include/linux/modversions.h: No such file or directory
In file included from memalloc.c:1:
memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/percpu.h:5,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/processor.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:48,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/asm-generic/percpu.h:8: error: 'CONFIG_NR_CPUS' undeclared here (not in a function)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/prefetch.h:14,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/list.h:8,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:48,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: 'CONFIG_X86_L1_CACHE_SHIFT' undeclared here (not in a function)
/lib/modules/2.6.20-16-generic/build/include/asm/processor.h:82: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/device.h:20,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/device.h:20,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'jiffies_to_msecs':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:274: error: for each function it appears in.)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:280:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'jiffies_to_usecs':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:285: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:293:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'msecs_to_jiffies':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:298: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:306:46: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'usecs_to_jiffies':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:311: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'timespec_to_jiffies':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:330: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:336: error: 'SHIFT_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'jiffies_to_timespec':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:349: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'timeval_to_jiffies':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:371: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:375: error: 'SHIFT_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'jiffies_to_timeval':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:387: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:400:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'jiffies_to_clock_t':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:401: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'clock_t_to_jiffies':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:412: error: 'CONFIG_HZ' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:431:6: error: division by zero in #if
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h: In function 'jiffies_64_to_clock_t':
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:432: error: 'CONFIG_HZ' undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/rcupdate.h:41,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/device.h:20,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h:85: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/linux/mmzone.h:282: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/utsname.h:35,
                 from /lib/modules/2.6.20-16-generic/build/include/asm/elf.h:12,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:15,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/device.h:20,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/lib/modules/2.6.20-16-generic/build/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/module.h:21,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/device.h:20,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:52,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/pci.h:6,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:746,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/linux/mm.h: In function 'lowmem_page_address':
/lib/modules/2.6.20-16-generic/build/include/linux/mm.h:539: warning: implicit declaration of function '__page_to_pfn'
/lib/modules/2.6.20-16-generic/build/include/linux/mm.h:539: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-generic/build/include/asm/pci.h:41,
                 from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:746,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/asm/io.h: In function 'virt_to_phys':
/lib/modules/2.6.20-16-generic/build/include/asm/io.h:77: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
/lib/modules/2.6.20-16-generic/build/include/asm/io.h: In function 'phys_to_virt':
/lib/modules/2.6.20-16-generic/build/include/asm/io.h:95: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
In file included from /lib/modules/2.6.20-16-generic/build/include/linux/pci.h:746,
                 from memalloc.inc:10,
                 from memalloc.c:1:
/lib/modules/2.6.20-16-generic/build/include/asm/pci.h: In function 'pci_dac_dma_to_page':
/lib/modules/2.6.20-16-generic/build/include/asm/pci.h:72: warning: implicit declaration of function '__pfn_to_page'
/lib/modules/2.6.20-16-generic/build/include/asm/pci.h:72: warning: return makes pointer from integer without a cast
In file included from memalloc.inc:13,
                 from memalloc.c:1:
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h: At top level:
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h:697: error: redefinition of 'jiffies_to_msecs'
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:268: error: previous definition of 'jiffies_to_msecs' was here
In file included from memalloc.inc:13,
                 from memalloc.c:1:
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h:699:31: error: division by zero in #if
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h: In function 'jiffies_to_msecs':
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h:704: error: 'CONFIG_HZ' undeclared (first use in this function)
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h: At top level:
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h:716: error: redefinition of 'msecs_to_jiffies'
/lib/modules/2.6.20-16-generic/build/include/linux/jiffies.h:290: error: previous definition of 'msecs_to_jiffies' was here
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h:720:31: error: division by zero in #if
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h: In function 'msecs_to_jiffies':
/home/matt/Desktop/alsa-driver-1.0.11/include/adriver.h:725: error: 'CONFIG_HZ' undeclared (first use in this function)
memalloc.c: In function 'snd_malloc_pages':
memalloc.c:269: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
memalloc.c:269: warning: passing argument 1 of 'mark_pages' makes pointer from integer without a cast
memalloc.c: In function 'snd_free_pages':
memalloc.c:290: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
memalloc.c:290: warning: passing argument 1 of 'unmark_pages' makes pointer from integer without a cast
memalloc.c: In function 'snd_malloc_dev_pages':
memalloc.c:316: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
memalloc.c:316: warning: passing argument 1 of 'mark_pages' makes pointer from integer without a cast
memalloc.c: In function 'snd_free_dev_pages':
memalloc.c:333: error: 'CONFIG_PAGE_OFFSET' undeclared (first use in this function)
memalloc.c:333: warning: passing argument 1 of 'unmark_pages' makes pointer from integer without a cast
make[1]: *** [memalloc.o] Error 1
make[1]: Leaving directory `/home/matt/Desktop/alsa-driver-1.0.11/acore'
make: *** [compile] Error 1


gotta love that beautiful output anyway though.:)
I'll reply back if I get anything, this really is a great card if it would work :)

---

### Post by Yfrwlf on 2007-08-11
> **Ateoto said:**
> ...this really is a great card if it would work :)

Sorry for the pessimistic post, but not being able to use the card because their driver sucks in effect makes the card crappy. =P  It's good that they tried, I'm all for more hardware supporting Linux don't get me wrong, but I'd rather buy a card that had good Linux support that, you know, actually *worked*.  Paying $130 or so for a card because you saw that it says it supports Linux only to find out the drivers don't work, so you're screwed, is NOT cool.  Bluegears making that claim cost my friend money.  Maybe it was an honest mistake, but claiming something works when it doesn't is pretty shady/mean.  Maybe someone down at R&D should have tested the drivers a bit more before releasing them.

Regardless, I hope they get their act together and show some functioning support for Linux, and I hope they help you and everyone was who was unfortunate enough to buy their card, and in your case especially after you went to the trouble of pointing out their errors for them.

Yes, Linux is often a community effort, but if I pay for a card, I expect snappy support on *their* end, so lets hope you get it. :)

---

### Post by Ateoto on 2007-08-14
Haha, I'd definitely tend to agree with you, but I have one working in a Windows gaming machine, and it really is a nice card. I'd argue that it's their drivers that suck. 

Anyway, I might have made some headway in that department. Major emphasis on the "might" there. I looked at it while at work and tried to merge bgears cmi8788 drivers into a newer alsa build and I was able to configure, make, and make install into Ubuntu. However that was at work, when I get home I'll try to install it on the machine with the card and see what happens. I'm keeping my fingers crossed :)

I've never tinkered with configure scripts before, so my machine at home might burst into flames and consume  my apartment with me in it, but I'm hoping it just works.

Edit: Thats a big no go. I was able to ./configure, make, and make install without errors. But the card was not detected correctly. Worth a shot anyway, I'll keep snooping around and see what I can find.

---

### Post by leptons on 2007-08-19
Hello, first post + newb here.

I don't know much about linux... that is why I've installed Kubuntu on my computer trying to learn it.

However, I noticed that my sound card (a b-Enspirer) didn't really work, after some research I came across this. I am very disappointed that the linux driver that BGears doesn't really work for the moment.

Perhaps we can put some pressure on those guys to force them to make a good linux driver?

---

