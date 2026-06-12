---
title: "my fglrx issue"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by icky on 2006-12-03
ati radeon 200m running 8.24.8 drivers. compiled the drivers by making a distro-package (deb), installed it from there...
my bios are set to sideport+uma128mb, i've no clue what else could be the problem.

i'm on dapper64 (with turion64 mind you)

```
(EE) fglrx(0): V_BIOS address 0x0 out of range
(EE) fglrx(0): PreInitInt10 failed
SetVBEMode failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

i'm thinking i might've messed up somewhere in the installation, is there a guide for installing 8.24.8 binaries?

---

