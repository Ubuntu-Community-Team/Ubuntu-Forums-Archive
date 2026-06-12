---
title: "Nvidia driver kernel will not build."
date: 2012-06-29
forum: Multimedia Software
---

### Post by atkane on 2012-06-29
Hey all! Just got a fresh version of xubuntu installed on a desktop for my research lab, and was installing the nvidia drivers so that I could use CUDA, unfortunately, I am running into some problems.  The error I am getting is  ```
/tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv-linux.h:114:75: fatal error: asm/system.h: No such file or directory
``` this makes the whole installation fail, I searched and could not find this particular problem, and any help would be greatly appreciated. 
I'll just post the rest of the log in case i missed something else
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Jun 29 14:46:35 2012
installer version: 295.41

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 295.41.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/3.5.0-2-generic/build'
-> Kernel output path: '/lib/modules/3.5.0-2-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/3.5.0-2-generic/build SYSOUT=/lib/modules/3.5.0-2-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (             \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
   mkdir -p /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/.tmp_versions ; rm -f /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel
     cc -Wp,-MD,/tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.7/include  -I/usr/src/linux-headers-3.5.0-2-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include /usr/src/linux-headers-3.5.0-2-generic/include/linux/kconfig.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -W
   error-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -DCONFIG_AS_AVX=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -mno-avx -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.41\" -Wno-unused-function -Wuninitialized -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz5266/
   NVIDIA-Linux-x86_64-295.41/kernel/.tmp_nv.o /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv.c
   In file included from include/linux/kernel.h:19:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv-linux.h:38,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv.c:13:
   include/linux/bitops.h: In function ‘hweight_long’:
   include/linux/bitops.h:66:41: warning: signed and unsigned type in conditional expression [-Wsign-compare]
   In file included from /usr/src/linux-headers-3.5.0-2-generic/arch/x86/include/asm/uaccess.h:586:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv-linux.h:97,
                    from /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv.c:13:
   /usr/src/linux-headers-3.5.0-2-generic/arch/x86/include/asm/uaccess_64.h: In function ‘copy_from_user’:
   /usr/src/linux-headers-3.5.0-2-generic/arch/x86/include/asm/uaccess_64.h:53:6: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
   In file included from /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv.c:13:0:
   /tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv-linux.h: At top level:
   /tmp/selfgz5267/NVIDIA-Linux-x86_64-295.41/kernel/nv-linux.h:114:75: fatal error: asm/system.h: No such file or directory
   compilation terminated.
   make[3]: *** [/tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel/nv.o] Error 1
   make[2]: *** [_module_/tmp/selfgz5266/NVIDIA-Linux-x86_64-295.41/kernel] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.

```

---

