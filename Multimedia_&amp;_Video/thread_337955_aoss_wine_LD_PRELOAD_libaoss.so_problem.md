---
title: "aoss wine LD_PRELOAD libaoss.so problem"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by SuperEe on 2007-01-13
I can't seem to get aoss working with wine. I get this error:

```

ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

```

I have aoss installed with 
```

lrwxrwxrwx 1 root root    16 2007-01-13 17:28 /usr/lib/libaoss.so -> libaoss.so.0.0.0
lrwxrwxrwx 1 root root    16 2007-01-13 17:28 /usr/lib/libaoss.so.0 -> libaoss.so.0.0.0
-rwSr-Sr-- 1 root root 17960 2006-06-20 19:09 /usr/lib/libaoss.so.0.0.0

```

Wine starts up fine, but it uses OSS. I've tried to use fixes when people had trouble with flash in firefox etc with no avail. How can get libaoss.so preloaded?

---

