---
title: "[SOLVED] How can I clean my kernel so I don't get  Unknown symbol in module errors wi"
date: 2008-09-17
forum: Multimedia Software
---

### Post by covert on 2008-09-17
I think I have infected my kernel in some way with my current Mythbuntu 8.04 install. When I try to "make insmod" in the v4l-dvb dir I get " Unknown symbol in module" errors for most the modules.

I did a fresh install on another machine of Mythbuntu 8.04 and used the same v4l source and it works perfect. So I now have a system to compare with.

uname -a returns  2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linu on both machines.

I checked my /usr/src/linux-headers-2.6.24-16-generic and /usr/src/linux-headers-2.6.24-16 folder contents and they match on both machines.

I checked my /v4l-dvb source folder and they match on both machines.

I checked /lib/modules/2.6.24-16-generic and they match on both machines.

What files could be causing the errors in the kernel of "Unknown symbol in module" ?

Is there any way for me to run a command to check it ?

---

### Post by covert on 2008-09-17
In my case my problem file was
/boot/initrd.img-2.6.24-16-generic

I replaced it with the one from the good system and I could compile v4l and insmod it OK.

---

