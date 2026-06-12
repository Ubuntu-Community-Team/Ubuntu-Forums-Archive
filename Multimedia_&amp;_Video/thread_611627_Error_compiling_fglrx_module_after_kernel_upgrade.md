---
title: "Error compiling fglrx module after kernel upgrade"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by synd7 on 2007-11-13
So i've had fglrx 8.42 installed on the stock gutsy kernel and running fine. The problem started when i opted to compile the 2.6.23.1 kernel.

I compiled the kernel succesfully, rebooted and tried to rebuild the fglrx module when i got an error complaining about SLAB (i compiled the kernel with SLUB)

I tried recompiling the kernel with SLAB and got (as far as i can tell) the same error:
```
make[1]: Entering directory `/usr/src/modules/fglrx'
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[2]: Entering directory `/usr/src/linux-2.6.23.1'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:365: warning: initialisation from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c:366: warning: initialisation from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;fglrx_pci_suspend&#8217;:
/usr/src/modules/fglrx/firegl_public.c:799: warning: passing argument 1 of &#8216;firegl_pci_save_state&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;fglrx_pci_resume&#8217;:
/usr/src/modules/fglrx/firegl_public.c:841: warning: passing argument 1 of &#8216;firegl_pci_restore_state&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_check_pci&#8217;:
/usr/src/modules/fglrx/firegl_public.c:1990: warning: &#8216;pci_find_slot&#8217; is deprecated (declared at include/linux/pci.h:481)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pci_find_device&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2019: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:480)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_vm_test_and_clear_dirty&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2544: error: implicit declaration of function &#8216;ptep_test_and_clear_dirty&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pci_find_slot&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2852: warning: &#8216;pci_find_slot&#8217; is deprecated (declared at include/linux/pci.h:481)
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_request_irq&#8217;:
/usr/src/modules/fglrx/firegl_public.c:2962: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:64)
/usr/src/modules/fglrx/firegl_public.c:2962: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;__ke_pte_phys_addr_str&#8217;:
/usr/src/modules/fglrx/firegl_public.c:3536: error: implicit declaration of function &#8216;pte_read&#8217;
/usr/src/modules/fglrx/firegl_public.c:3538: error: implicit declaration of function &#8216;pte_exec&#8217;
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:5439: error: expected specifier-qualifier-list before &#8216;kmem_cache_t&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_Initialize&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5478: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;routine_type&#8217;
/usr/src/modules/fglrx/firegl_public.c:5479: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5480: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;name&#8217;
/usr/src/modules/fglrx/firegl_public.c:5484: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5485: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;name&#8217;
/usr/src/modules/fglrx/firegl_public.c:5485: error: too many arguments to function &#8216;kmem_cache_create&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_Destroy&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5508: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5518: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5520: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_AllocEntry&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5555: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;routine_type&#8217;
/usr/src/modules/fglrx/firegl_public.c:5556: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5580: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5583: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5591: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;KAS_SlabCache_FreeEntry&#8217;:
/usr/src/modules/fglrx/firegl_public.c:5619: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;routine_type&#8217;
/usr/src/modules/fglrx/firegl_public.c:5620: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
/usr/src/modules/fglrx/firegl_public.c:5632: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;cache&#8217;
/usr/src/modules/fglrx/firegl_public.c:5635: error: &#8216;kasSlabCache_t&#8217; has no member named &#8216;lock&#8217;
make[3]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[2]: *** [_module_/usr/src/modules/fglrx] Error 2
make[2]: Leaving directory `/usr/src/linux-2.6.23.1'
make[1]: *** [build] Error 2
make[1]: Leaving directory `/usr/src/modules/fglrx'
Module /usr/src/modules/fglrx failed.

```

Note: that error was from when i compiled the kernel the second time (i'm pretty sure its the same as the first one though)

Any ideas?

Edit: i downgraded to 2.6.22-rt and i'm getting the same error

Edit2: turns out the 8.42 driver doesnt have 2.6.23 support and the -rt kernel was compiled with paravirtualization support which causes errors. i recompiled the -rt kernel without paravirtualization and its all going well

---

### Post by mzw! on 2007-11-15
how do you re.compile the rt kernel? is there any guide or something? I tried to do so but I was unable to build fglrx after that and I thought I recompile the rt kernel without paravirtualization.

Thank you in advance

---

### Post by macabro22 on 2007-12-14
Is there no easier way?

---

