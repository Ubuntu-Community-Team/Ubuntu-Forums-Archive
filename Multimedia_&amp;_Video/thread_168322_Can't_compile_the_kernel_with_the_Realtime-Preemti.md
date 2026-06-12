---
title: "Can't compile the kernel with the Realtime-Preemtion patch"
date: 2006-04-30
forum: Multimedia &amp; Video
---

### Post by Shimonn on 2006-04-30
Hi.

I followed this : [http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Dapper:Vanilla_Kernel_With_Realtime_Preemption) but when compiling (make-kpkg ...) i've this error.
```
[...]
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
mm/built-in.o : Dans la fonction "__free_pages_ok":page_alloc.c:(.text+0x620a): référence indéfinie vers « debug_check_no_locks_freed »
mm/built-in.o : Dans la fonction "kfree": référence indéfinie vers « debug_check_no_locks_freed »
make[1]: *** [.tmp_vmlinux1] Erreur 1
make[1]: quittant le répertoire « /usr/src/linux-2.6.16.11-rt »
make: *** [stamp-build] Erreur 2
```
which roughly means that there is an "undefined reference" to *debug_check_no_locks_freed* in the function *__free_pages_ok* of the *mm/page_alloc.c* file.

What can i do ?

Thanks for your help.

Edit : I'm using [the kernel version 2.6.16.11]("http://www.kernel.org/") and [the patch version 2.6.16-rt18]("http://people.redhat.com/mingo/realtime-preempt/patch-2.6.16-rt18")

---

### Post by Shimonn on 2006-04-30
I answer myelf :
First, when applying the patch, i had some errors. I answered not to apply the patch on the files that would fail (the default).
I retried with answering to apply the patch anyway, and the compilation went fine.

---

