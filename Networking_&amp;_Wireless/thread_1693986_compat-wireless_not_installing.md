---
title: "compat-wireless not installing"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by blake1324 on 2011-02-23
i cant seem to install compat-wireless on my netbook i have done it previously but it is not working this time

> make: gcc: Command not found
make: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
make -C /lib/modules/2.6.35-22-generic/build M=/home/blake/compat-wireless-2.6.38-rc4-1 modules
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-22-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
/usr/src/linux-headers-2.6.35-22-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  LD      /home/blake/compat-wireless-2.6.38-rc4-1/compat/built-in.o
/bin/sh: ar: not found
make[3]: *** [/home/blake/compat-wireless-2.6.38-rc4-1/compat/built-in.o] Error 127
make[2]: *** [/home/blake/compat-wireless-2.6.38-rc4-1/compat] Error 2
make[1]: *** [_module_/home/blake/compat-wireless-2.6.38-rc4-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [modules] Error 2

this is what i keep getting

---

### Post by drewesq on 2011-04-19
I am having this problem too with natty....

Hope someone can help?!

---

