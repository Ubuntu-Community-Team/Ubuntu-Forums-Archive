---
title: "Lynxtwo OSS  soundcard install on Ubuntu 22.04.02"
date: 2023-03-24
forum: Multimedia Software
---

### Post by davetherave1 on 2023-03-24
Hi, I re-purposed my Vortexbox server by installing Ubuntu in view of usingmy Lynx TWO soundcard.
I downloaded the oss driver file from Open Sound and tried to install but his the following problem.
Any advice how i can proceed from here. 
Thanks

============================
Setting up oss-linux (4.2-2020) ...
Building OSS Modules for Linux-x86_64 5.15.0-67-generic


OSS build environment set up for REGPARM kernels


Building module osscore
Failed to compile OSS
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
make -C /lib/modules/5.15.0-67-generic/build M=/usr/lib/oss/build modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-67-generic'
  CC [M]  /usr/lib/oss/build/osscore_lnk.o
/usr/lib/oss/build/osscore_lnk.c: In function ‘oss_get_time’:
/usr/lib/oss/build/osscore_lnk.c:89:10: error: implicit declaration of function ‘get_seconds’ [-Werror=implicit-function-declaration]
   89 |   return get_seconds ();
      |          ^~~~~~~~~~~
/usr/lib/oss/build/osscore_lnk.c: In function ‘alloc_fop’:
/usr/lib/oss/build/osscore_lnk.c:1012:15: warning: unused variable ‘tmp_compat_ioctl’ [-Wunused-variable]
 1012 |   new_ioctl_t tmp_compat_ioctl = (new_ioctl_t) op->compat_ioctl;
      |               ^~~~~~~~~~~~~~~~
/usr/lib/oss/build/osscore_lnk.c:1011:15: warning: unused variable ‘tmp_unlocked_ioctl’ [-Wunused-variable]
 1011 |   new_ioctl_t tmp_unlocked_ioctl = (new_ioctl_t) op->unlocked_ioctl;
      |               ^~~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:297: /usr/lib/oss/build/osscore_lnk.o] Error 1
make[1]: *** [Makefile:1906: /usr/lib/oss/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-67-generic'
make: *** [Makefile:21: default] Error 2
Forcing re-detection of installed soundcards
Starting Open Sound System
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
Relinking OSS kernel modules for ""
This may take few moments - please stand by...


OSS build environment set up for REGPARM kernels


Building module osscore
Failed to compile OSS
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/zfs/zfs.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/i915/i915.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
/lib/modules/5.15.0-67-generic/kernel/drivers/gpu/drm/amd/amdgpu/amdgpu.ko is too large
make -C /lib/modules/5.15.0-67-generic/build M=/usr/lib/oss/build modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-67-generic'
  CC [M]  /usr/lib/oss/build/osscore_lnk.o
/usr/lib/oss/build/osscore_lnk.c: In function ‘oss_get_time’:
/usr/lib/oss/build/osscore_lnk.c:89:10: error: implicit declaration of function ‘get_seconds’ [-Werror=implicit-function-declaration]
   89 |   return get_seconds ();
      |          ^~~~~~~~~~~
/usr/lib/oss/build/osscore_lnk.c: In function ‘alloc_fop’:
/usr/lib/oss/build/osscore_lnk.c:1012:15: warning: unused variable ‘tmp_compat_ioctl’ [-Wunused-variable]
 1012 |   new_ioctl_t tmp_compat_ioctl = (new_ioctl_t) op->compat_ioctl;
      |               ^~~~~~~~~~~~~~~~
/usr/lib/oss/build/osscore_lnk.c:1011:15: warning: unused variable ‘tmp_unlocked_ioctl’ [-Wunused-variable]
 1011 |   new_ioctl_t tmp_unlocked_ioctl = (new_ioctl_t) op->unlocked_ioctl;
      |               ^~~~~~~~~~~~~~~~~~
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:297: /usr/lib/oss/build/osscore_lnk.o] Error 1
make[1]: *** [Makefile:1906: /usr/lib/oss/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-67-generic'
make: *** [Makefile:21: default] Error 2


Relinking the OSS kernel modules failed

---

### Post by davetherave1 on 2023-03-26
Anyone have a clue please?

---

### Post by Holger_Gehrke on 2023-03-26
AFAIK the Open Sound System has not been part of the Linux Kernel for some time now (early 2000s if memory serves ...), being replaced with ALSA (Advanced Linux Sound Architecture) because OSS was trying to go commercial. The version of oss available from opensound.com is for the 4.x series of kernels. The last updates in their mercurial version control seem to be from 2012. It might not be dead, but it certainly isn't doing too well.

Holger

---

### Post by davetherave1 on 2023-03-26
> **Holger_Gehrke said:**
> AFAIK the Open Sound System has not been part of the Linux Kernel for some time now (early 2000s if memory serves ...), being replaced with ALSA (Advanced Linux Sound Architecture) because OSS was trying to go commercial. The version of oss available from opensound.com is for the 4.x series of kernels. The last updates in their mercurial version control seem to be from 2012. It might not be dead, but it certainly isn't doing too well.

Holger
Thanks Holger
Is it possible to install and that kernel version (for development) just to get the installation completed then use the driver in the latest kernel....might be a stupid question but just trying to find a way.
Thanks

---

### Post by Holger_Gehrke on 2023-03-27
AFAIK kernel modules are version specific. A module has to be compiled with the headers for a specific kernel to work with that kernel.

There is some OSS compatibility built into ALSA, but it's meant for programs that are written to use OSS and not for drivers.

The [compatibility-Matrix at alsa.org]("https://alsa-project.org/wiki/Matrix:Vendor-Lynx_Studio_Technology") lists the LynxTWO with the "Unsupported" tag, which means "Hardware is not supported due to lack of documentation from the hardware vendor."

Holger

---

### Post by davetherave1 on 2023-03-28
Ok thanks. Sounds like the Lynx drivers cant be installed.

---

