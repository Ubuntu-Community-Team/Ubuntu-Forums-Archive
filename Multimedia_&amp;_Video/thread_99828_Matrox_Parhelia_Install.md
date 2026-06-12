---
title: "Matrox Parhelia Install"
date: 2005-12-06
forum: Multimedia &amp; Video
---

### Post by alan1974us on 2005-12-06
Hi guys, I'm a linux newbie who's trying to install Matrox's Parhelia driver in 5.10. After receiving the need GCC 3.4.4 errors, I followed some instructions on how to install gcc 3.4 and now I get an error that I can't figure out. If anyone can help me with the make.log it would be much appreciated.:confused: 

[SIZE="1"]Using kernel headers in /lib/modules/2.6.12-9-386/build//include for kernel version 2.6.x
making all in /parhelia...
make[1]: Entering directory `/home/abeza/matroxdriver/kernel/src/parhelia'
gcc  -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default   -c MtxParhlParms.c -o MtxParhlParms.o
In file included from /lib/modules/2.6.12-9-386/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-386/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-386/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-386/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-386/build//include/linux/module.h:10,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:49,
                 from MtxParhlParms.c:19:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h: In function ‘prefetch_range’:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in arithmetic
In file included from /lib/modules/2.6.12-9-386/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-386/build//include/linux/pci.h:864,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:56,
                 from MtxParhlParms.c:19:
/lib/modules/2.6.12-9-386/build//include/asm/io.h: In function ‘check_signature’:
/lib/modules/2.6.12-9-386/build//include/asm/io.h:253: warning: wrong type argument to increment
make[1]: Leaving directory `/home/abeza/matroxdriver/kernel/src/parhelia'
making all in /mtxvxd...
make[1]: Entering directory `/home/abeza/matroxdriver/kernel/src/mtxvxd'
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxCpu.c -o MtxCpu.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxCs.c -o MtxCs.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxIo.c -o MtxIo.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxMem.c -o MtxMem.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxMsr.c -o MtxMsr.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxPci.c -o MtxPci.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxTimer.c -o MtxTimer.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxMap.c -o MtxMap.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxDte.c -o MtxDte.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxLdt.c -o MtxLdt.o
MtxLdt.c: In function ‘ldtRead’:
MtxLdt.c:104: warning: assignment makes pointer from integer without a cast
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxLdtr.c -o MtxLdtr.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxGdt.c -o MtxGdt.o
MtxGdt.c: In function ‘gdtRead’:
MtxGdt.c:102: warning: assignment makes pointer from integer without a cast
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxGdtr.c -o MtxGdtr.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/abeza/matroxdriver/kernel/src/../include -I/home/abeza/matroxdriver/kernel/src/../include/mtxvxd -I/home/abeza/matroxdriver/kernel/src -I/home/abeza/matroxdriver/kernel/src/parhelia -I/home/abeza/matroxdriver/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-386/build//include -I/lib/modules/2.6.12-9-386/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxDbg.c -o MtxDbg.o
ld -r MtxCpu.o MtxCs.o MtxIo.o MtxMem.o MtxMsr.o MtxPci.o MtxTimer.o MtxMap.o MtxDte.o MtxLdt.o MtxLdtr.o MtxGdt.o MtxGdtr.o MtxDbg.o -o mtxvxd.o
make[1]: Leaving directory `/home/abeza/matroxdriver/kernel/src/mtxvxd'
make -C /lib/modules/2.6.12-9-386/build/ SUBDIRS=/home/abeza/matroxdriver/kernel/src MTXMODDIR=/home/abeza/matroxdriver/kernel/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/abeza/matroxdriver/kernel/src/mtx_drv.o
In file included from /lib/modules/2.6.12-9-386/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-386/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-386/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-386/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-386/build//include/linux/module.h:10,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:49,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.c:17:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h: In function ‘prefetch_range’:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in arithmetic
In file included from /lib/modules/2.6.12-9-386/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-386/build//include/linux/pci.h:864,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:56,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.c:17:
/lib/modules/2.6.12-9-386/build//include/asm/io.h: In function ‘check_signature’:
/lib/modules/2.6.12-9-386/build//include/asm/io.h:253: warning: wrong type argument to increment
  CC [M]  /home/abeza/matroxdriver/kernel/src/mtx_dev.o
In file included from /lib/modules/2.6.12-9-386/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-386/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-386/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-386/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-386/build//include/linux/module.h:10,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:49,
                 from /home/abeza/matroxdriver/kernel/src/mtx_dev.c:18:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h: In function ‘prefetch_range’:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in arithmetic
In file included from /lib/modules/2.6.12-9-386/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-386/build//include/linux/pci.h:864,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:56,
                 from /home/abeza/matroxdriver/kernel/src/mtx_dev.c:18:
/lib/modules/2.6.12-9-386/build//include/asm/io.h: In function ‘check_signature’:
/lib/modules/2.6.12-9-386/build//include/asm/io.h:253: warning: wrong type argument to increment
/home/abeza/matroxdriver/kernel/src/mtx_dev.c: In function ‘mtx_dev_init’:
/home/abeza/matroxdriver/kernel/src/mtx_dev.c:395: warning: passing argument 1 of ‘ClientPciConfigReadDword’ makes integer from pointer without a cast
  CC [M]  /home/abeza/matroxdriver/kernel/src/mtx_ctx.o
In file included from /lib/modules/2.6.12-9-386/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-386/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-386/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-386/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-386/build//include/linux/module.h:10,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:49,
                 from /home/abeza/matroxdriver/kernel/src/mtx_ctx.c:18:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h: In function ‘prefetch_range’:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in arithmetic
In file included from /lib/modules/2.6.12-9-386/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-386/build//include/linux/pci.h:864,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:56,
                 from /home/abeza/matroxdriver/kernel/src/mtx_ctx.c:18:
/lib/modules/2.6.12-9-386/build//include/asm/io.h: In function ‘check_signature’:
/lib/modules/2.6.12-9-386/build//include/asm/io.h:253: warning: wrong type argument to increment
  CC [M]  /home/abeza/matroxdriver/kernel/src/mtx_mem.o
In file included from /lib/modules/2.6.12-9-386/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-386/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-386/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-386/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-386/build//include/linux/module.h:10,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:49,
                 from /home/abeza/matroxdriver/kernel/src/mtx_mem.c:17:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h: In function ‘prefetch_range’:
/lib/modules/2.6.12-9-386/build//include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in arithmetic
In file included from /lib/modules/2.6.12-9-386/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-386/build//include/linux/pci.h:864,
                 from /home/abeza/matroxdriver/kernel/src/mtx_drv.h:56,
                 from /home/abeza/matroxdriver/kernel/src/mtx_mem.c:17:
/lib/modules/2.6.12-9-386/build//include/asm/io.h: In function ‘check_signature’:
/lib/modules/2.6.12-9-386/build//include/asm/io.h:253: warning: wrong type argument to increment
/home/abeza/matroxdriver/kernel/src/mtx_mem.c: At top level:
/home/abeza/matroxdriver/kernel/src/mtx_mem.c:31: warning: initialization makes integer from pointer without a cast
/home/abeza/matroxdriver/kernel/src/mtx_mem.c: In function ‘mtx_mem_alloc_agp’:
/home/abeza/matroxdriver/kernel/src/mtx_mem.c:195: warning: passing argument 1 of ‘agp_allocate_memory’ makes pointer from integer without a cast
/home/abeza/matroxdriver/kernel/src/mtx_mem.c:195: error: too few arguments to function ‘agp_allocate_memory’
make[2]: *** [/home/abeza/matroxdriver/kernel/src/mtx_mem.o] Error 1
make[1]: *** [_module_/home/abeza/matroxdriver/kernel/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2
[/SIZE]

---

