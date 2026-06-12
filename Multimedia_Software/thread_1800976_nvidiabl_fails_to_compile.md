---
title: "nvidiabl fails to compile"
date: 2011-07-09
forum: Multimedia Software
---

### Post by FlamingSpaz on 2011-07-09
Hey guys, I'm having a problem compiling nvidiabl-0.69 on my VPCCW1S1E. It's running 10.10 x64

```
Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-30-generic -C /lib/modules/2.6.35-30-generic/build SUBDIRS=/var/lib/dkms/nvidiabl/0.69/build modules....(bad exit status: 2)
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidiabl-dkms.0.crash'
Error! Bad return status for module build on kernel: 2.6.35-30-generic (x86_64)
Consult /var/lib/dkms/nvidiabl/0.69/build/make.log for more information.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module
cleaning build area....
make KERNELRELEASE=2.6.35-30-generic -C /lib/modules/2.6.35-30-generic/build SUBDIRS=/var/lib/dkms/nvidiabl/0.69/build modules....(bad exit status: 2)
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidiabl-dkms.0.crash'
Error! Bad return status for module build on kernel: 2.6.35-30-generic (x86_64)
Consult /var/lib/dkms/nvidiabl/0.69/build/make.log for more information.

```make.log

```
DKMS make.log for nvidiabl-0.69 for kernel 2.6.35-30-generic (x86_64)
Sun Jul 10 00:45:10 BST 2011
make: Entering directory `/usr/src/linux-headers-2.6.35-30-generic'
  CC [M]  /var/lib/dkms/nvidiabl/0.69/build/nvidiabl-module.o
/var/lib/dkms/nvidiabl/0.69/build/nvidiabl-module.c:37: warning: #warning USE_BACKLIGHT_SUSPEND
  CC [M]  /var/lib/dkms/nvidiabl/0.69/build/nvidiabl-models.o
/var/lib/dkms/nvidiabl/0.69/build/nvidiabl-models.c:178: error: ‘nv5x_resto2500000re’ undeclared here (not in a function)
make[1]: *** [/var/lib/dkms/nvidiabl/0.69/build/nvidiabl-models.o] Error 1
make: *** [_module_/var/lib/dkms/nvidiabl/0.69/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-30-generic'

```Any help is greatly appreciated.

---

### Post by papernik on 2011-09-11
Same error here, is there any solution ?

thanks

---

