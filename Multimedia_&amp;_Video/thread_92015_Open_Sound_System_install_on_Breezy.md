---
title: "Open Sound System install on Breezy"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by suppos on 2005-11-18
hi,

I have a problem with my Riptide sound card. I know that it is not natively supported by Linux, so I have tried to install Open Sound System from 4Front. It worked on Ubuntu Hoary, but on the latest Breezy it stops in the middle of install and spits out the following log at me =(

As I am a relatively a new linux user, so I cannot see the cause of this problem. I thought that it might be because of the wrong version of GCC  (last 2 lines of the log). So i have tried to change the compiler:

#apt-get install gcc-3.4
#CC = gcc-3.4
#export CC

, but it still output the same log afterwards =(

So my questions are:
   1) What should I do next in order to get my soundcard working?
   2) Is there someone patient enough to take through a new linux user aka me through this process?tnx,
paul

```
Fri Nov 18 18:54:20 GMT 2005
Kernel version: Linux tuxbox 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
Modutils version: 3.2-pre7
 18:54:20 up  1:57,  3 users,  load average: 0.37, 0.26, 0.46
=== Running ./bin/soundconf ===
Install directory: /usr/lib/oss
Will use /usr/bin/ld for linking.
Will use /usr/bin/X11/ld for linking.
Will use /usr/bin/ld for linking.
make -C /lib/modules/`uname -r`/source scripts scripts_basic include/linux/version.h
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: Nothing to be done for `scripts_basic'.
  CHK     include/linux/version.h
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make -C /lib/modules/`uname -r`/source SUBDIRS=/usr/lib/oss/kbuild CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /usr/lib/oss/kbuild/osslinux.o
/usr/lib/oss/kbuild/osslinux.c: In function ‘__moddi3’:
/usr/lib/oss/kbuild/osslinux.c:1639: warning: pointer targets in passing argument 3 of ‘__udivmoddi4’ differ in signedness
  Building modules, stage 2.
  MODPOST
*** Warning: "oss_checksum" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_init_module" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "touch_mixer" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_version_string" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_cardlist" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_cleanup_module" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "num_mididevs" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "oss_mixer_ext" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
*** Warning: "mixer_ext_set_enum" [/usr/lib/oss/kbuild/osslinux.ko] undefined!
  CC      /usr/lib/oss/kbuild/osslinux.mod.o
  LD [M]  /usr/lib/oss/kbuild/osslinux.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
rm -f *.o *.ko *.mod.c
The kbuild method worked OK
/usr/bin/ld -r -o /usr/lib/oss/modules/osslinux /usr/lib/oss/modules/sndshield /usr/lib/oss/modules/soundbase /usr/lib/oss/modules/pnp /usr/lib/oss/modules/sb /usr/lib/oss/modules/ad1848 /usr/lib/oss/modules/cs4232 /usr/lib/oss/modules/opl3sa -L./lib -ldrivers
Loading OSS/Linux module
insmod: error inserting '/usr/lib/oss/modules/osslinux': -1 Invalid module format
insmod: error inserting '/usr/lib/oss/modules/osslinux': -1 Invalid module format
The osslinux module didnt load. Cannot continue.
  echo The osslinux module didnt load. Cannot continue.
[4294761.222000] Bluetooth: RFCOMM socket layer initialized
[4294761.222000] Bluetooth: RFCOMM TTY layer initialized
[4294761.950000] usbcore: deregistering driver speedtch
[4294762.178000] CSLIP: code copyright 1989 Regents of the University of California
[4294762.210000] PPP generic driver version 2.4.2
[4294806.420000] HDLC line discipline: version $Revision: 4.8 $, maxframe=4096
[4294806.420000] N_HDLC line discipline registered.
[4294806.601000] NET: Registered protocol family 10
[4294806.601000] Disabled Privacy Extensions on device c02eb280(lo)
[4294806.602000] IPv6 over IPv4 tunneling driver
[4296445.536000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4296445.536000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4296445.656000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4296445.656000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300719.870000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300719.870000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300720.020000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300720.020000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[B][4301741.986000] osslinux: version magic '2.6.12 386 gcc-4.0' should be '2.6.12-9-386 386 gcc-3.4'
[4301742.039000] osslinux: version magic '2.6.12 386 gcc-4.0' should be '2.6.12-9-386 386 gcc-3.4'[/B]
```

---

### Post by thoerner on 2006-04-24
i am having the same problem, just thought i'd post a reply to bump the message... i hope someone can help! thanks in advance!

---

### Post by adamkane on 2006-04-24
Looks like an issue with hoary/gcc-3.4 vs breezy/gcc-4.0.

You probably have to tell configure that you want to use gcc-3.4.

I forget, but something like this?:
```

./configure --CC=gcc-3.4

```

---

