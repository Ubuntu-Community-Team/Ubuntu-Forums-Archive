---
title: "Problems compiling ALSA"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Geezle on 2008-02-03
To make a short story long, I have no sound, and I'm trying to recompile ALSA with the module for my sound device, but I'm running into problems as soon as I try to compile alsa-drivers.  I get the following output when I try to compile 

```

jay@jay-desktop:/usr/src/alsa-driver-1.0.9$ sudo make
[sudo] password for jay:
make[1]: Entering directory `/usr/src/alsa-driver-1.0.9/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/usr/src/alsa-driver-1.0.9/include  -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/usr/src/alsa-driver-1.0.9/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /usr/src/alsa-driver-1.0.9/include/adriver.h:45,
                 from /usr/src/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /usr/src/alsa-driver-1.0.9/include/adriver.h:45,
                 from /usr/src/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/desc.h:11,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/elf.h:50,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:15,
                 from /usr/src/alsa-driver-1.0.9/include/adriver.h:45,
                 from /usr/src/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:93: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:305: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,
                 from /usr/src/alsa-driver-1.0.9/include/adriver.h:45,
                 from /usr/src/alsa-driver-1.0.9/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/module.h:64:2: error: #error unknown processor family
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/irq.h:176: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa-driver-1.0.9/acore'
make: *** [compile] Error 1

```
I've made sure I have all my headers and build-essential installed and I'm all out of ideas.

I'm a bit of a linux newb so I may have very easily missed something.  I would really appreciate any ideas/help you folks can offer.

Thanks

---

### Post by Yellow Pasque on 2008-02-03
Why are you trying to build 1.0.9? That's really old! What sound hardware do you have? Run this for me if you don't know:
```
sudo update-pciids; lspci
cat /proc/asound/card0/codec#* | grep Codec
```
I also have some scripts that compile the latest version of ALSA if you're using a High-Def onboard sound chip (compliant with Intel Azalia standard). They can also be modified for other sound modules.

---

### Post by Geezle on 2008-02-04
My audio device is :  Ensoniq 5880 AudioPCI (rev 04)

I'm not entirely sure why I'm using such an old version of ALSA either...I guess it's the first version I stumbled across.

---

### Post by Yellow Pasque on 2008-02-04
It looks like it's not finding your headers. Go to System -> Administration -> Synaptic and make sure you have the linux-headers-2.6.22-14 and linux-headers-2.6.22-14-headers-generic packages installed

BTW, Your card uses the ens1371 driver.

---

### Post by Geezle on 2008-02-04
It's amazing...if you use the proper, up to date ALSA files, they compile properly.  

Sometimes I just need the obvious pointed out to me.  Thanks for the help guys, everything seems all sorted out for the moment and my sound is working again. :)

---

