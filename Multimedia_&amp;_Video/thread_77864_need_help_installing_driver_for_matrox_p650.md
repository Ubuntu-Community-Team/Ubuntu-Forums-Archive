---
title: "need help installing driver for matrox p650"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by lndbrusr on 2005-10-17
Hello,

I have downloaded the 1.4.1 mtxdriver for the matrox p650 card from Matrox' site.

I have also installed the linux-header for my kernel rev.

When I run the driver install (sudo /bin/sh mtxdriver-1.4.1_pro.run), I get the following:
========================================
   Matrox Linux Driver Install Script
========================================

Currently installed driver is the same as the installer file.
X server driver not installed.

Messages are being logged in file make.log,
this might take some time.

Compiling mtx.ko ...
ERROR: There has been an error compiling the kernel module.
       A log file has been created in the file make.log

The program returned an error code (1)
s390082@d11007808:/tmp$

Part of the exit on the script removes all files from the /tmp/mtx/ directory where I told the script to expand to for the install so there is no log file.

Can someone assist?

thanks,
cj

---

### Post by rps63ifid on 2005-10-21
I wish I had more to offer in the way of help, but I have run into exactly the same problem. I had no problems getting it installed, etc., under 5.04 but no joy yet under 5.10...

---

### Post by Mehster on 2005-10-24
Not that this helps any, but I am also having the same problem.  It is keeping me from using Kubuntu at work as I have dual monitors with one dark :(

---

### Post by rps63ifid on 2005-11-08
OK...

I had a little time to play with this some more, and although not yet successful, I did get a little further and I am hoping that someone may be able to move me a little closer to getting this to work.

After downloading the driver package for the P650 from [www.matrox.com](www.matrox.com), I ran the following commands:

sudo -i
sh ./mtxdriver-1.4.1_pro.run

It stopped almost immediately, and the make.log file in folder matroxdriver- had the following line:

./install.sh: line 731: make: command not found

Sure enough, I didn't have make installed. Installed make via synaptic, and re-ran the 'sh ./mtxdriver-1.4.1_pro.run' command above. It took longer, but still no joy. This is what the make.log file now contains:

```
Using kernel headers in /lib/modules/2.6.12-9-686/build//include for kernel version 2.6.x
making all in /parhelia...
make[1]: Entering directory `/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia'
gcc  -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default   -c MtxParhlParms.c -o MtxParhlParms.o
In file included from /lib/modules/2.6.12-9-686/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-686/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-686/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-686/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-686/build//include/linux/module.h:10,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:49,
                 from MtxParhlParms.c:19:
/lib/modules/2.6.12-9-686/build//include/linux/prefetch.h: In function 'prefetch_range':
/lib/modules/2.6.12-9-686/build//include/linux/prefetch.h:62: warning: pointer of type 'void *' used in arithmetic
In file included from /lib/modules/2.6.12-9-686/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-686/build//include/linux/pci.h:864,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:56,
                 from MtxParhlParms.c:19:
/lib/modules/2.6.12-9-686/build//include/asm/io.h: In function 'check_signature':
/lib/modules/2.6.12-9-686/build//include/asm/io.h:253: warning: wrong type argument to increment
make[1]: Leaving directory `/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia'
making all in /mtxvxd...
make[1]: Entering directory `/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtxvxd'
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxCpu.c -o MtxCpu.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxCs.c -o MtxCs.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxIo.c -o MtxIo.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxMem.c -o MtxMem.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxMsr.c -o MtxMsr.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxPci.c -o MtxPci.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxTimer.c -o MtxTimer.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxMap.c -o MtxMap.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxDte.c -o MtxDte.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxLdt.c -o MtxLdt.o
MtxLdt.c: In function 'ldtRead':
MtxLdt.c:104: warning: assignment makes pointer from integer without a cast
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxLdtr.c -o MtxLdtr.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxGdt.c -o MtxGdt.o
MtxGdt.c: In function 'gdtRead':
MtxGdt.c:102: warning: assignment makes pointer from integer without a cast
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxGdtr.c -o MtxGdtr.o
gcc    -D__KERNEL__ -DOS_LINUX -Wpointer-arith -Wcast-align -Wno-missing-braces -Wno-sign-compare     -O2 -fomit-frame-pointer -finline-functions -DMODULE -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/../include/mtxvxd -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia -I/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/parhelia/Main -I/lib/modules/2.6.12-9-686/build//include -I/lib/modules/2.6.12-9-686/build//include/asm/mach-default  -D__NO_VERSION__ -c MtxDbg.c -o MtxDbg.o
ld -r MtxCpu.o MtxCs.o MtxIo.o MtxMem.o MtxMsr.o MtxPci.o MtxTimer.o MtxMap.o MtxDte.o MtxLdt.o MtxLdtr.o MtxGdt.o MtxGdtr.o MtxDbg.o -o mtxvxd.o
make[1]: Leaving directory `/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtxvxd'
make -C /lib/modules/2.6.12-9-686/build/ SUBDIRS=/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src MTXMODDIR=/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src modules
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.o
In file included from /lib/modules/2.6.12-9-686/build//include/asm/system.h:5,
                 from /lib/modules/2.6.12-9-686/build//include/asm/processor.h:18,
                 from /lib/modules/2.6.12-9-686/build//include/asm/thread_info.h:17,
                 from /lib/modules/2.6.12-9-686/build//include/linux/thread_info.h:21,
                 from /lib/modules/2.6.12-9-686/build//include/linux/spinlock.h:12,
                 from /lib/modules/2.6.12-9-686/build//include/linux/capability.h:45,
                 from /lib/modules/2.6.12-9-686/build//include/linux/sched.h:7,
                 from /lib/modules/2.6.12-9-686/build//include/linux/module.h:10,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:49,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.c:17:
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:10:20: error: stdarg.h: No such file or directory
In file included from /lib/modules/2.6.12-9-686/build//include/asm/system.h:5,
                 from /lib/modules/2.6.12-9-686/build//include/asm/processor.h:18,
                 from /lib/modules/2.6.12-9-686/build//include/asm/thread_info.h:17,
                 from /lib/modules/2.6.12-9-686/build//include/linux/thread_info.h:21,
                 from /lib/modules/2.6.12-9-686/build//include/linux/spinlock.h:12,
                 from /lib/modules/2.6.12-9-686/build//include/linux/capability.h:45,
                 from /lib/modules/2.6.12-9-686/build//include/linux/sched.h:7,
                 from /lib/modules/2.6.12-9-686/build//include/linux/module.h:10,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:49,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.c:17:
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:94: error: syntax error before 'va_list'
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:95: warning: function declaration isn't a prototype
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:98: error: syntax error before 'va_list'
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:99: warning: function declaration isn't a prototype
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:102: error: syntax error before 'va_list'
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:103: warning: function declaration isn't a prototype
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:107: error: syntax error before 'va_list'
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:108: warning: function declaration isn't a prototype
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:119: error: syntax error before 'va_list'
/lib/modules/2.6.12-9-686/build//include/linux/kernel.h:120: warning: function declaration isn't a prototype
In file included from /lib/modules/2.6.12-9-686/build//include/linux/list.h:7,
                 from /lib/modules/2.6.12-9-686/build//include/linux/wait.h:23,
                 from /lib/modules/2.6.12-9-686/build//include/asm/semaphore.h:41,
                 from /lib/modules/2.6.12-9-686/build//include/linux/sched.h:20,
                 from /lib/modules/2.6.12-9-686/build//include/linux/module.h:10,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:49,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.c:17:
/lib/modules/2.6.12-9-686/build//include/linux/prefetch.h: In function 'prefetch_range':
/lib/modules/2.6.12-9-686/build//include/linux/prefetch.h:62: warning: pointer of type 'void *' used in arithmetic
In file included from /lib/modules/2.6.12-9-686/build//include/linux/dmapool.h:14,
                 from /lib/modules/2.6.12-9-686/build//include/linux/pci.h:864,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:56,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.c:17:
/lib/modules/2.6.12-9-686/build//include/asm/io.h: In function 'check_signature':
/lib/modules/2.6.12-9-686/build//include/asm/io.h:253: warning: wrong type argument to increment
In file included from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.h:75,
                 from /home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.c:17:
/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_client.h: At top level:
/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_client.h:70: error: syntax error before 'va_list'
/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_client.h:70: warning: function declaration isn't a prototype
/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_client.h:71: error: syntax error before 'va_list'
/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_client.h:71: warning: function declaration isn't a prototype
make[2]: *** [/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src/mtx_drv.o] Error 1
make[1]: *** [_module_/home/ron/Documents/Downloads/Matrox/matroxdriver-/kernel/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make: *** [default] Error 2
```

Can someone help me figure out what is missing or wrong here?

Thanks in advance!

---

### Post by mOjO_420 on 2006-02-19
well.. i might be a bit late but you also need to do:

apt-get install gcc-3.4

at least it compiled for me with gcc-3.4 but not gcc-4
and of course i'm using latest mtx driver which is newer...

---

### Post by drucer on 2006-04-05
Check out my post on another thread. You might find some help there.

[http://www.ubuntuforums.org/showthread.php?t=113797&highlight=matrox+p650](http://www.ubuntuforums.org/showthread.php?t=113797&highlight=matrox+p650)

---

