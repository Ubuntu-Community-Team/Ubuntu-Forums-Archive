---
title: "modprobe invalid argument with ltserial"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by walom on 2006-05-10
I'm trying to set up my old Winbook Si2 with Ubuntu. I have an LT lucent winmodem, I read through how to get the drivers for it but when I try to go

```
$ sudo modprobe ltmodem
$ lsmod | grep lt
ltmodem                 565872  0
cfbimgblt                   2944  2 vesafb.vgal6fb
```

```
$ Sudo modprobe ltserial
FATAL: Error inserting ltserial (/lib/modules/2.6.12-9-386/extra/ltserial.ko): Invalid argument

```
I've done everthing else:
Installed Kernel Headers for my Kernel
Installed gcc-3.4 and symlinked it to /usr/bin/gcc
checked to make sure that ltmodem.ko and ltserial.ko exist in /lib/module/2.6.12-9-386/extra

Does anybody know how to fix this?
I'm pretty new to linux so please explain thoroughly, thanks

---

