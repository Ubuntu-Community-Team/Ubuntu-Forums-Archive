---
title: "Sound broken after kernel headers upgrade"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by ulink on 2007-12-20
Hi all,

A few minutes ago I updated my system from the update manager. Some of the packages were updated kernel headers (2.6.22-14-generic).

After a reboot the sound doesn't work. No sound device is found. I am using Ubuntu 7.10 and the sound card is build in the motherboard.

I tried to run alsamixer and it gives me this error:
alsamixer: function snd_ctl_open failed for default: No such device

Then I run `strace -eopen alsamixer` and I got:
open("/etc/ld.so.cache", O_RDONLY)      = 3
open("/lib/libncurses.so.5", O_RDONLY)  = 3
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
open("/dev/snd/controlC0", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("/dev/aloadC0", O_RDONLY)          = -1 ENOENT (No such file or directory)

Does anyone know a way out of this?

---

### Post by fuzzypig on 2007-12-20
please run "sudo depmod" and then reboot.

It seems that the developers forgot to add the depmod command to the end of one of the update packages, which prevents most of the kernel modules from being found after the latest kernel update.

---

### Post by ulink on 2007-12-21
Thanks for the answer! :)
I found a solution before reading your answer.

I installed linux-backports-modules after reading about [Bug #131133](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/131133), rebooted and it now works good.

---

### Post by kyllikki on 2007-12-23
I am experiencing the same issues with sound after running the automatic update and rebooting.  The above suggestion for running depmod did not work for me and I am not keen to try the backporting fix because my sound was fine before the automatic updates ran.  Any other suggestions would be greatly appreciated.

---

