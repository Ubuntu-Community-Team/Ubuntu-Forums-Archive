---
title: "Problems with ATI fglrx 8.18.8"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by carsten on 2005-11-08
Hi
I installed the fglrx driver on my 64 bit ubuntu, and it worked flawlesly. Then, due to some packages not being 64 bit yet, it switched back to ubuntu 32 bit. Here, I had to compile a new kernel du to clock skew problems, so I used vanilla 2.6.14. Now it wont compile the fglrx kernel module. Here is what is have in /usr/share/fglrx/fglrx-install.log:

```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.14-ck1/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-2.6.14cK1'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function ‘__fgl_agp_init’:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8173: warning: ‘pm_register’ is deprecated (declared at include/linux/pm.h:107)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function ‘__fgl_agp_cleanup’:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8183: warning: ‘pm_unregister_all’ is deprecated (declared at include/linux/pm.h:117)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6077: warning: ‘ati_gart_base’ defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:135:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:243:5: warning: "FIREGL_VMA_INFO" is not defined
In file included from /lib/modules/fglrx/build_mod/2.6.x/drm_proc.h:41,
                 from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:297:
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:561:5: warning: "__HAVE_VBL_IRQ" is not defined
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:664:5: warning: "__HAVE_VBL_IRQ" is not defined
/lib/modules/fglrx/build_mod/2.6.x/drmP.h:936:5: warning: "__HAVE_SG" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:371:5: warning: "FIREGL_VMA_INFO" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:388:5: warning: "FIREGL_VMA_INFO" is not defined
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘firegl_stub_putminor’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:542: warning: ‘inter_module_put’ is deprecated (declared at include/linux/module.h:573)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:544: warning: ‘inter_module_unregister’ is deprecated (declared at include/linux/module.h:570)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘firegl_stub_register’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:564: warning: ‘inter_module_register’ is deprecated (declared at include/linux/module.h:569)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:595: warning: ‘inter_module_put’ is deprecated (declared at include/linux/module.h:573)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_verify_area’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1478: warning: implicit declaration of function ‘verify_area’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘do_vm_kmap_nopage’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2465: warning: assignment makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘__ke_smp_call_function’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3754: warning: statement with no effect
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
*** Warning: "verify_area" [/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko] undefined!
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-2.6.14cK1'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

```

I the following howto for installing fglrx:
[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

I have also tried to disabled Direct Rendering Manager in the kernel. I could not disable agp gart for some reason....

Hope you can help

---

### Post by mlomker on 2005-11-08
I was looking through the [Rage3D forum]("www.rage3d.com/board/forumdisplay.php?f=88") and there are some patches required for 2.6.14.  You'll want to take a look at that.

---

