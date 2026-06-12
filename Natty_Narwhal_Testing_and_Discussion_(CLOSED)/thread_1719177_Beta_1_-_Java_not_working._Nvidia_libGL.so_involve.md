---
title: "Beta 1 - Java not working. Nvidia libGL.so involved. Means no netbeans!"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by barisurum on 2011-04-01
trying to launch netbeans 6.9.1 creates this hs_err_pid.log:

```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007f789b0b7d21, pid=12225, tid=140156229072640
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK 64-Bit Server VM (20.0-b11 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.10.1pre
# Distribution: Ubuntu Natty (development branch), package 6b22-1.10.1~pre1-0ubuntu1
# Problematic frame:
# C  [libGL.so.1+0x7dd21]  glXCreateWindow+0xeb01
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
#
```

No netbeans mean no job, hunger and social disorder!

---

### Post by dino99 on 2011-04-01
sun-java6-jre 6.24: partner repo

---

### Post by barisurum on 2011-04-01
> sun-java6-jre 6.24: partner repo

I'm happy to say this proprietary runtime from SUN Microsystems (Oracle) works very well. I hope OpenJDK can do well too when natty gets released. Thank you dino99, you saved a family from starvation :P

---

### Post by dino99 on 2011-04-01
> **barisurum said:**
> I'm happy to say this proprietary runtime from SUN Microsystems (Oracle) works very well. I hope OpenJDK can do well too when natty gets released. Thank you dino99, you saved a family from starvation :P

Oracle have made lot of work on JRE, fixing so old bugs left behind a few years by SUN. Openjdk is far behind sadly (but its younger too )

have a good WE

---

