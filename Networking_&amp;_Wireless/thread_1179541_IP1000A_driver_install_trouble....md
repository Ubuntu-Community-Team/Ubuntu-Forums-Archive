---
title: "IP1000A driver install trouble..."
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by aafree on 2009-06-05
Hey all!
I did a fresh install of Ubuntu 8.04-2-server (2.6.24-23) onto a US15W Atom system that has a IC Plus IP1000A nic.  I installed gcc and the supplied linux headers on the install disc.  When I "make all" for the network driver, as oulined in the readme from the nic driver zip file, it fails with the error:
make[1]: ***no rule to make target 'arch/x86/kernel/asm-offset.c', needed by 'arch/x86/kernel/asm-offset.s'

When I search for the file "$ find / -name offset*" it doesn't exist, it finds the following:
/usr/src/linux-headers-2.6.24-23-server/arch/x86/kernel/asm-offset.s
/usr/src/linux-headers-2.6.24-23-server/include/asm-x86/asm-offset.h

That's it, no C source file.  I'm dazed and confused right now from the lump on my head (you should see the wall!) left from my frustration. If anyone has insight to a solution, please help me~!

---

### Post by chili555 on 2009-06-05
I haven't run 8.04 in some time, however my system contains *ipg.ko*. Does 8.04? If so, please try:```
sudo modprobe ipg
```If you downloaded IP1000A, version 2.10c, it was built in September of 2007, probably too old to be usable.

---

