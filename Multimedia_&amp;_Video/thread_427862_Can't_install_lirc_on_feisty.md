---
title: "Can't install lirc on feisty"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by vondo on 2007-04-29
I've been trying to follow the instructions at

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

First, this doesn't say how to install the linux sources which is needed, right? To try to fulfill that, I do the following

install the .deb linux-sources
bunzip2 and untar the .bz2 file installed in /usr/src
link -s linux to the directory tree created by the untar
go into linux/ and make oldconfig && make prepare

Then start in on the instructions on the page above:
the command "m-a a-i lirc" is the stage where things fail. The log then shows

```

/usr/bin/make -f scripts/Makefile.build obj=/usr/src/modules/lirc/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/usr/src/modules/lirc/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isyst
em /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/lin
ux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-str
ict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2
 -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i38
6/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statemen
t -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/u
sr/src/modules/lirc/drivers/lirc_dev/../.. -I/lib/modules/2.6.20-15-generic/build/include
/ -I/lib/modules/2.6.20-15-generic/build/drivers/media/video/  -DMODULE -D"KBUILD_STR(s)=
#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c
-o /usr/src/modules/lirc/drivers/lirc_dev/.tmp_lirc_dev.o /usr/src/modules/lirc/drivers/l
irc_dev/lirc_dev.c
In file included from include/linux/sched.h:68,
                 from include/linux/utsname.h:35,
                 from include/asm/elf.h:12,
                 from include/linux/elf.h:7,
                 from include/linux/module.h:15,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/securebits.h:1:1: warning: null character(s) ignored
include/linux/securebits.h:1:1177: warning: no newline at end of file
In file included from include/linux/sched.h:75,
                 from include/linux/utsname.h:35,
                 from include/asm/elf.h:12,
                 from include/linux/elf.h:7,
                 from include/linux/module.h:15,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/seccomp.h:1:1: warning: null character(s) ignored
include/linux/seccomp.h:1:791: warning: no newline at end of file
In file included from include/linux/utsname.h:35,
                 from include/asm/elf.h:12,
                 from include/linux/elf.h:7,
                 from include/linux/module.h:15,
                 from /usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.c:36:
include/linux/sched.h:952: error: expected specifier-qualifier-list before ‘seccomp_t’
include/linux/sched.h: In function ‘task_lock’:
include/linux/sched.h:1480: error: ‘struct task_struct’ has no member named ‘alloc_lock’
include/linux/sched.h: In function ‘task_unlock’:
include/linux/sched.h:1485: error: ‘struct task_struct’ has no member named ‘alloc_lock’
make[6]: *** [/usr/src/modules/lirc/drivers/lirc_dev/lirc_dev.o] Error 1
make[5]: *** [_module_/usr/src/modules/lirc/drivers/lirc_dev] Error 2

```

Has anyone gotten this to work or does anyone know what the problem is?

---

