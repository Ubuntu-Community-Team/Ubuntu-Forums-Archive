---
title: "nvidia graphics card support"
date: 2012-05-02
forum: Multimedia Software
---

### Post by bpb101 on 2012-05-02
what operating systems bit do nvidia THEMSELF support. Is it just 86 bit or do they support 32 and 64?

---

### Post by BicyclerBoy on 2012-05-02
I assume you mean nVidia driver support direct from their driver download server..

Both, there are x86_64 **&** i386 versions. (AMD64 & intel32).
Note: There are dependencies, read the driver readme..

The 64bit driver installer optionally builds the 32bit openGL support but only if the 32 bit build libraries are installed (ia32-libs).

The 32 bit openGL support is/was required by programs like Wine etc..

---

