---
title: "m9xdriver-x86_64-1.2.6 - field ‘struct_mutex’ has incomplete type"
date: 2010-12-05
forum: Multimedia Software
---

### Post by STOIE on 2010-12-05
Hi all,

As per my title I am trying to upgrade to the latest Matrox driver for my M9148 card.
I run x86_64 Maverick and have had to hold back on the new Xorg because of the drivers not supporting the Maverick release version.
Now, Matrox have put together a new driver which is supposed to support the new Xorg, however, when running the complile, I get the following errors in the log:

```

rm -f /home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/KernelLibraries.o_shipped
ln -s /home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/KernelLibraries.o_shipped /home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/KernelLibraries.o_shipped
make -C /lib/modules/2.6.35-22-generic/build  M=/home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src    EXTRA_CFLAGS="-I/home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/include -I/home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/common"
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/built-in.o
  CC [M]  /home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/m9x_base.o
In file included from /home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/m9x_base.c:9:
/home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/m9x_base.h:97: error: field ‘struct_mutex’ has incomplete type
make[2]: *** [/home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src/m9x_base.o] Error 1
make[1]: *** [_module_/home/anlocal/m9xdriver-x86_64-1.2.6-20101110/kernel/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2


```


Please note system specs are:
Ubuntu Maverick 10.10 x86_64
Matrox M9148LP
m9xdriver-x86_64-1.2.6

Any help would be appreciated.

Thanks,
./aaron

---

### Post by msch on 2010-12-08
I'm on Debian, but same issue.  I was able to get the driver to compile by hopping back to kernel 2.6.32.  I'm still working on getting things working under 2.6.36.

The driver supports X.org 7.5, but I'm guessing the kernel is too new, I think you're at 2.6.34 on mav.

---

### Post by bryan headley on 2011-11-04
Of course you could fix the driver source so it builds. Matrox says they have new drivers about to be released in the next couple of weeks. RSN

---

