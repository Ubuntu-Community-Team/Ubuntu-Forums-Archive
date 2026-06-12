---
title: "Netpbm 10.26.45 make error 1 &amp; 2"
date: 2009-04-21
forum: Multimedia Software
---

### Post by Ecologger on 2009-04-21
Hey all I was attempting to compile netpbm, yes I know it is in the repositories but I need a tool not with that package, and when I go to execute make it throws me an error:

"libpbm3.c: In function ‘packBitsWithMmxSse’:
libpbm3.c:108: warning: specifying vector types with __attribute__ ((mode)) is deprecated
libpbm3.c:108: warning: use __attribute__ ((vector_size)) instead
libpbm3.c:117: note: use -flax-vector-conversions to permit conversions between vectors with differing element types or numbers of subparts
libpbm3.c:117: error: incompatible type for argument 1 of ‘__builtin_ia32_pcmpeqb’
libpbm3.c:117: error: incompatible type for argument 2 of ‘__builtin_ia32_pcmpeqb’
libpbm3.c:117: error: incompatible types in initialization
libpbm3.c:119: error: incompatible type for argument 1 of ‘__builtin_ia32_pmovmskb’
make[1]: *** [libpbm3.o] Error 1
make[1]: Leaving directory `/home/User/Desktop/netpbm-10.26.45/lib'
make: *** [lib/all] Error 2"

I'm not sure how to fix it. Any advice would be appreciated.

---

