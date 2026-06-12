---
title: "Problems installing Realtek drivers"
date: 2011-01-18
forum: Multimedia Software
---

### Post by JayDSee on 2011-01-18
Hi all,

I'm a newbie and could use a little help.  I'm running Ubuntu 10.10  on an ASUS A8N-E motherboard with onboard sound. The problem is that I don't get any sound output.  Ubuntu indicate that is has found internal hardware and has configured it. But, alas no sound.

I've downloaded the Realtek v2.7 sound drivers and am trying to install them.  When I run "./configure" I see the following warnings:

checking for GCC version... ./configure: eval: line 3442: syntax error near unexpected token `)'
./configure: eval: line 3442: `my_compiler_version=4.4.4-14ubuntu5)'
./configure: line 3442: warning: syntax errors in . or eval will cause future versions of the shell to abort as Posix requires
Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.


When I run "make" I get the following:

jesse@jesse-Linux:~/Downloads/alsa-driver-1.0.4$ make
make[1]: Entering directory `/home/jesse/Downloads/alsa-driver-1.0.4/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/jesse/Downloads/alsa-driver-1.0.4/include  -I/lib/modules/2.6.35-24-generic/build/include -O2  -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include   -DEXPORT_SYMTAB -c hwdep.c
In file included from hwdep.c:22:
/home/jesse/Downloads/alsa-driver-1.0.4/include/sound/driver.h:29: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[1]: *** [hwdep.o] Error 1
make[1]: Leaving directory `/home/jesse/Downloads/alsa-driver-1.0.4/acore'
make: *** [compile] Error 1

It seemed that it couldn't find the directory or file.  But, I checked and both exist.

Any guidance would be appreciated.

Jesse

---

