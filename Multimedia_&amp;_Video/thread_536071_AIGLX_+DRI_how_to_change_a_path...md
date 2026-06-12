---
title: "AIGLX +DRI how to change a path.."
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by Beyo on 2007-08-27
Hello
I have strange error noticed in xorg.0.log
```
(==) AIGLX enabled
(EE) AIGLX error: dlopen of /home/felix/src/snapshots/inst/HEAD/lib/dri/i915_dri.so failed (/home/felix/src/snapshots/inst/HEAD/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(EE) AIGLX error: dlopen of /home/felix/src/snapshots/inst/HEAD/lib/dri/i915_dri.so failed (/home/felix/src/snapshots/inst/HEAD/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering

```
problem is i never had /home/felix on my computer so i dont know why aiglx search for *.so file in that directory.
How to change it? is it needed to set up some system variable?
i have tis *.so file in /usr/lib/dri

---

### Post by Beyo on 2007-08-29
It seems nobody wants to help...:(

---

### Post by Offoffoff on 2007-09-04
I confirm this.... I have the same message in xorg.0.log.... I have Radeon driver on ATI IGP 330/340/350...

---

