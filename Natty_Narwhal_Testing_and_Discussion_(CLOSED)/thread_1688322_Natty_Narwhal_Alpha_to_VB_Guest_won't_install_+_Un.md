---
title: "Natty Narwhal Alpha to VB Guest won't install + Unity broken"
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2011-02-15
Just installed Natty Narwhal Alpha two as I would really like to do some testing and see Unity 3D at work. Did to the installation of the Desktop and did all updates. Two issues no. VBx Guest Installation says I miss headers and has this in error logs:
```
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -Wp,-MD,/tmp/vbox.0/.VBoxGuest-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i686-linux-gnu/4.5.2/include  -I/usr/src/linux-headers-2.6.38-3-generic/arch/x86/include -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/lib/modules/2.6.38-3-generic/build/include -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -I/tmp/vbox.0/vboxguest/ -I/tmp/vbox.0/vboxguest/include -I/tmp/vbox.0/vboxguest/r0drv/linux -D__KERNEL__ -DMODULE -DVBOX -DRT_OS_LINUX -DIN_RING0 -DIN_RT_R0 -DIN_GUEST -DIN_GUEST_R0 -DIN_MODULE -DRT_WITH_VBOX -DVBGL_VBOXGUEST -DVBOX_WITH_HGCM -DRT_ARCH_X86  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(VBoxGuest_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxguest)" -c -o /tmp/vbox.0/.tmp_VBoxGuest-linux.o /tmp/vbox.0/VBoxGuest-linux.c
In file included from /tmp/vbox.0/r0drv/linux/the-linux-kernel.h:34:0,
                 from /tmp/vbox.0/VBoxGuest-linux.c:27:
/tmp/vbox.0/include/iprt/types.h:105:31: fatal error: linux/autoconf.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vbox.0/VBoxGuest-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxguest] Error 2
```

I do have the headers though:
```
sudo apt-get install linux-headers-`uname  -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.38-3-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any idea how to fix this?

Other issue that Unity 3D is not working at all and that the Gome Desktop bars are shown as gray ones. See screenshot. For the latter I wonder for what Gnome part I should file a bug. Any tips for what Linux/Ubuntu part I should run ubuntu-bug..

---

### Post by MadCow108 on 2011-02-15
install the guest additions from the repository. they are patched for kernel 38
sudo apt-get install virtualbox-ose-guest*

here is the patch that fixes this particular problem:
[http://git.debian.org/?p=pkg-virtualbox/virtualbox-ose.git;a=blob;f=debian/patches/30-kernel-2.6.38.diff;h=31a51295c886c823666ddc9b7c5a0de8fa2965ea;hb=HEAD](http://git.debian.org/?p=pkg-virtualbox/virtualbox-ose.git;a=blob;f=debian/patches/30-kernel-2.6.38.diff;h=31a51295c886c823666ddc9b7c5a0de8fa2965ea;hb=HEAD)

the other problem could be related to 3dsupport in the virtual box not working (without guest-additions?)
does the classic desktop work?

---

### Post by Stoneface on 2011-02-15
Just installed VBox Guest Addition from the repository. No luck. Checking your adjusted post now.

---

### Post by Stoneface on 2011-02-15
> **MadCow108 said:**
> install the guest additions from the repository. they are patched for kernel 38
sudo apt-get install virtualbox-ose-guest*

I ran ```
sudo apt-get install virtualbox-ose-guest*
``` And said yes to X11 change during that process, restarted. Vbox started out really big and did initially not resize, but after logging in Unity 3D was there and resizing worked :-) Thanks a lot MadCow108!

P.S. Reading  [http://git.debian.org/?p=pkg-virtualbox/virtualbox-ose.git;a=blob;f=debian/patches/30-kernel-2.6.38.diff;h=31a51295c886c823666ddc9b7c5a0de8fa2965ea;hb=HEAD](http://git.debian.org/?p=pkg-virtualbox/virtualbox-ose.git;a=blob;f=debian/patches/30-kernel-2.6.38.diff;h=31a51295c886c823666ddc9b7c5a0de8fa2965ea;hb=HEAD) as well.

---

