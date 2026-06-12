---
title: "Help with RTL8185, can't &quot;make&quot; a driver..."
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by pvfjr on 2010-06-08
I'm having some issues with my RTL8185 on a fresh install of Lucid on a quad core x64.  It connects, but the signal strength is much weaker than it should be.  I did some searching and found others with the same problem, but couldn't find any solutions.  First off, I have build-essentials, and the kernel headers.  I downloaded the latest drivers off the realtek website, started following their directions and got this on the first step:

```
pvfjr@acer-desktop:~/Desktop/rtl8185$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.o
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c: In function ‘proc_get_stats_hw’:
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:350: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:351: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:354: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:355: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:358: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:359: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c: In function ‘check_tx_ring’:
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:826: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:826: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:827: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:827: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c: In function ‘alloc_tx_desc_ring’:
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:1447: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:1447: warning: cast to pointer from integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c: In function ‘alloc_rx_desc_ring’:
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:1621: warning: cast from pointer to integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:1621: warning: cast to pointer from integer of different size
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c: In function ‘rtl8180_rx’:
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:2065: error: implicit declaration of function ‘rdtsc_rtl’
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c: In function ‘rtl8180_watch_dog’:
/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.c:2793: warning: unused variable ‘bEnterPS’
make[2]: *** [/home/pvfjr/Desktop/rtl8185/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/pvfjr/Desktop/rtl8185/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2
pvfjr@acer-desktop:~/Desktop/rtl8185$ 

```

I also tried following the directions on the rtl-wifi project page, though I couldn't find a date on anything and it seemed like it might be a little old.  It gave me similar errors anyway.

```
 pvfjr@acer-desktop:~/rtl-wifi$ sudo make
make -C /lib/modules/2.6.32-22-generic/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [modules] Error 2


```

Any ideas?  This is my main everyday use computer, and it's getting a connection speed of 1Mbps, pretty sucky. I'd hate to have to go back to win7...

---

### Post by xproject on 2010-07-12
I know this thread is old, but I ran into this issue recently on Lucid and I think I figured it out. I have **not** tried this with any type of encryption (WPA, WEP).

I am not sure how much you know about C/C++, so I will explain alittle bit. The error you are getting is because the function `rdtsc_rtl` is not explicitly defined. This is happening most likely because you are on a 64bit version of Linux (rdtsc_rtl is inside a block of #ifdef __i386__). I too have a 64bit version installed. So, what you need to do is edit the file rtl8180/r8180_core.c, find the lines that says `#ifdef __i386__` and change it to: `#ifndef __i386__`. Perform a `make clean` and then follow the readme, starting with `make`.

Also, make sure to blacklist the rtl8180 driver. You can find out how to do this through a google/forum search.

I hope this helps and isn't too late.

---

### Post by .dave on 2010-11-25
well this is a problem for me as i have this wireless card and i think the generic drivers that came with my lucid are th cause of all my woes. 

therefore I'm going to attempt to do as you have said and will report back if it works. if not I'll keep hunting my poor heart out.

---

### Post by mockingbird on 2011-02-09
> **xproject said:**
> I know this thread is old, but I ran into this issue recently on Lucid and I think I figured it out. I have **not** tried this with any type of encryption (WPA, WEP).

I am not sure how much you know about C/C++, so I will explain alittle bit. The error you are getting is because the function `rdtsc_rtl` is not explicitly defined. This is happening most likely because you are on a 64bit version of Linux (rdtsc_rtl is inside a block of #ifdef __i386__). I too have a 64bit version installed. [COLOR="Red"]So, what you need to do is edit the file rtl8180/r8180_core.c, find the lines that says `#ifdef __i386__` and change it to: `#ifndef __i386__`.[/COLOR] Perform a `make clean` and then follow the readme, starting with `make`.

Also, make sure to blacklist the rtl8180 driver. You can find out how to do this through a google/forum search.

I hope this helps and isn't too late.

GOLD!  Thanks.  I couldn't understand why it wouldn't compile on my 64-bt Squeeze.  FINALLY this works great and the driver loads fine.  The RTL8180 that comes default is nowhere near as good as the one from Realtek's website.

---

### Post by jonaternet on 2011-09-05
"I hope this helps and isn't too late."*

No, the problem is unfortunately still actual, so thanks a lot ! :-D

---

