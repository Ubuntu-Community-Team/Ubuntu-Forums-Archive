---
title: "Latest libbluray 0.7.0 -- BDJ cannot find main classes"
date: 2015-02-01
forum: Multimedia Software
---

### Post by Georges_Koyer on 2015-02-01
Hi there,

I am currently trying to compile and run the latest version of libbluray and test its BD-J capabilities.
Although the library compiles and installs without errors, the example programmes (bdj_test) throw exceptions, because no class can be registered at all.

The first line of the rather long traceback reads:
```

register_native.c:37: Failed to locate class org/videolan/Logger
Exception in thread "main" java.lang.NoClassDefFoundError: org/videolan/Logger
Caused by: java.lang.ClassNotFoundException: org.videolan.Logger

```

This goes on with almost all classes.
I suspect, there is something wrong with my Java-Installation.
```

java version "1.7.0_75"
OpenJDK Runtime Environment (IcedTea 2.5.4) (7u75-2.5.4-1~trusty1)
OpenJDK 64-Bit Server VM (build 24.75-b04, mixed mode)

```

Although, it works at least so far that the test programmes don't complain about not finding libbluray.jar.
Thus the all important question: How can I treat Java to actually look inside the jar-File?

Koyer.

---

