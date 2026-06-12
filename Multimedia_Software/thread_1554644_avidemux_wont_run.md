---
title: "avidemux wont run"
date: 2010-08-17
forum: Multimedia Software
---

### Post by bobdobbs on 2010-08-17
Hi all.

I'd love to be able to edit video on ubuntu. 
A while back I tried to get lives to work on ubuntu, but after much effort, it still refused to initialize properly.

I'd like to take a shot with avidemux.
I've installed it via apt-get.

However, when I try to run it from the commandline, I get this error:

```

avidemux: error while loading shared libraries: libfusion-1.0.so.0: cannot open shared object file: No such file or directory

```

It appears that I have libfusion. 
```
locate libfusion
``` returns:
```
/usr/lib/libfusion-1.2.so.0
/usr/lib/libfusion-1.2.so.0.8.0
/usr/lib/libfusion.a
/usr/lib/libfusion.so
/usr/lib/googleearth/libfusioncommon.so
```

Is there a way to get avidemux running on ubuntu without downgrading libfusion?

---

### Post by bobdobbs on 2010-08-17
Damn - I've just found other problems related to that error.

I wanted to mess around with Spring - the awesome looking strategy game.

I installed it with apt-get ages ago. 
I just tried to run it, and I get the same error:

```

spring: error while loading shared libraries: libfusion-1.0.so.0: cannot open shared object file: No such file or directory

```

Seems to me like something related to these libraries is broken.
Is this just my system? Or do other people have it too?

---

