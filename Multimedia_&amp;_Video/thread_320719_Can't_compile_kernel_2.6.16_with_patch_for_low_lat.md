---
title: "Can't compile kernel 2.6.16 with patch for low latency"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by finferflu on 2006-12-17
Hi everybody,

Today I've been trying to compile the kernel 2.6.16 with Ingo Molnar's patch for low latency, but I was unsuccessful.

I've been following this wiki: [https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption](https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption) but I get the following error when I run the command **make-kpkg --revision 1 --initrd kernel_image kernel_headers modules_image**:

```
exec debian/rules  DEBIAN_REVISION=1  INITRD=YES  kernel_image kernel_headers modules_image
include/asm/byteorder.h:5:28: error: linux/compiler.h: No such file or directory
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x588): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x837): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0x9b0): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xbd2): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x40ac): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x53cb): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make: *** [debian/stamp-build-kernel] Error 2
```

I'm no expert, so I don't even know what that could possibly mean, anyway I've saved a log, and I attach it to this post, just in case.

Thanks a lot!

---

### Post by finferflu on 2006-12-18
Sorry to bump, but anyone there who can possibly help me please?
Thanks.

---

### Post by memeplex on 2006-12-19
As you are on edgy you should install gcc-3.x package and then build the kernel with
MAKEFLAGS="CC=gcc-3.x" make-kpkg ...

---

### Post by finferflu on 2006-12-19
ah! thanks for the reply, but somebody has already made a precompiled version available. Thanks for your hint anyway, it may come useful to someone else.

Sorry for me forgetting to post that I found a solution..

---

