---
title: "alsa upgrade script"
date: 2009-08-30
forum: Multimedia Software
---

### Post by Gooksn on 2009-08-30
Hi! I just ran the "alsa upgrade script" first with option "-d" following option "-snap". Unfortunately the script is just running to...:
```
make[1]: Entering directory `/usr/src/linux-headers-2.6.29.4'
/usr/src/linux-headers-2.6.29.4/arch/x86/Makefile:41: /usr/src/linux-headers-2.6.29.4/arch/x86/Makefile_32.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.29.4/arch/x86/Makefile_32.cpu'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29.4'
make: *** [compile] Error 2
alsa-driver-1.0.20 make failed
```Am I doing something wrong? I'd appreciate if someone would help me out of here! :)

Greets Gooksn

---

### Post by zob on 2009-08-31
Did you run both commands as root (sudo)? I think you have to.

---

