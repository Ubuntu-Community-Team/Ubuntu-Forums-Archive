---
title: "Minecraft crashed on map loading"
date: 2011-10-25
forum: Multimedia Software
---

### Post by morpheus_sar on 2011-10-25
Hey guys. I've recently installed minecraft on my PC.I use this loader for mc: acminecraft. As driver for my AMD HD4870 I use official one with flgrx. 

```

ka2m@mypc:/$ java -version
java version "1.6.0_29"
Java(TM) SE Runtime Environment (build 1.6.0_29-b11)
Java HotSpot(TM) Server VM (build 20.4-b02, mixed mode)
ka2m@mypc:/$ 

```
My OS is Ubuntu 11.10:
```

ka2m@mypc:/$ uname -a
Linux mypc 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 i686 i386 GNU/Linux

```
LWJGL is installed, all libraries were downloaded from  lwjgl's site. But still

```

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb78af424, pid=10674, tid=1848212336
#
# JRE version: 6.0_29-b11
# Java VM: Java HotSpot(TM) Server VM (20.4-b02 mixed mode linux-x86 )
# Problematic frame:
# C[thread 1845422960 also had an error]
  [+0x424]  __kernel_vsyscall+0x10
#

```

---

