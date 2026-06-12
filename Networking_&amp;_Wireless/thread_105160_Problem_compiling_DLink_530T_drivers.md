---
title: "Problem compiling DLink 530T drivers"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by The Belgain on 2005-12-17
Hi there, dunno if this is the right subforum to post in, seeing as this isn't really a network issue, but a compiling issue.

I'm trying to build the DLink 530T driver (i.e. the sk98lin driver available from [here]("http://www.dlink.com/products/support.asp?pid=284&")), but am hitting errors due to it not picking up certain header files.

I've followed the instructions in the kernel install guide, but the header files it's complaining about just seem to be missing from the kernel source directory.  I've attached the build log (bzipped).

Could someone give me a hand?  I'm getting similar problems trying to compile the drivers for my Highpoint 1540 SATA card...

Cheers.

---

### Post by The Belgain on 2005-12-18
And just to save people the hassle of looking at the log file; here are the header files which are reported as missing:

```
/usr/src/linux/include/linux/thread_info.h:21:29: error: asm/thread_info.h: No such file or directory
/usr/src/linux/include/linux/kernel.h:17:21: error: asm/bug.h: No such file or directory
/usr/src/linux/include/asm-i386/processor.h:22:24: error: asm/percpu.h: No such file or directory
/usr/src/linux/include/linux/jiffies.h:9:23: error: asm/div64.h: No such file or directory
/usr/src/linux/include/linux/string.h:24:24: error: asm/string.h: No such file or directory
/usr/src/linux/include/linux/wait.h:27:25: error: asm/current.h: No such file or directory
/usr/src/linux/include/linux/rwsem.h:27:65: error: asm/rwsem.h: No such file or directory
/usr/src/linux/include/linux/sched.h:24:25: error: asm/cputime.h: No such file or directory
/usr/src/linux/include/linux/topology.h:34:26: error: asm/topology.h: No such file or directory
/usr/src/linux/include/linux/seccomp.h:11:25: error: asm/seccomp.h: No such file or directory
/usr/src/linux/include/linux/module.h:21:23: error: asm/local.h: No such file or directory
/usr/src/linux/include/asm-i386/irq.h:16:25: error: irq_vectors.h: No such file or directory
/usr/src/linux/include/asm-i386/hw_irq.h:19:26: error: asm/sections.h: No such file or directory
/usr/src/linux/include/linux/dmapool.h:15:29: error: asm/scatterlist.h: No such file or directory
/usr/src/linux/include/linux/pci.h:904:21: error: asm/pci.h: No such file or directory
/usr/src/linux/include/linux/mm.h:36:25: error: asm/pgtable.h: No such file or directory
/usr/src/linux/include/linux/highmem.h:12:25: error: asm/highmem.h: No such file or directory
/usr/src/linux/include/linux/poll.h:12:25: error: asm/uaccess.h: No such file or directory

```

Any idea why these aren't in the linux source directory I unpacked?

---

### Post by The Belgain on 2005-12-18
Well, I noticed that most of those files were in the directory, but under architecture-specific subdirectories.  So I created a symbolic link from to point to the asm-i386 directory, which seems to have fixed most of these errors.

I'm still seeing one error; it isn't finding irq_vectors.h.  Again, this file seems to be there, but not where it's expecting it.

Am I missing something here?  Surely it's not intended that files need to be moved around in the kernel source tree just to be able to compile the driver for a network card?  Is there a step I'm missing after having unpacked the kernel source?  I haven't actually compiled the kernel, as I'm not intending to use a different kernel, I just want to build a new module...

---

