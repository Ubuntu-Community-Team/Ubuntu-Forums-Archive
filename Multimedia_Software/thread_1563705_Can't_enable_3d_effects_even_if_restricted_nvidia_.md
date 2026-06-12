---
title: "Can't enable 3d effects even if restricted nvidia driver is installed"
date: 2010-08-29
forum: Multimedia Software
---

### Post by uFrank on 2010-08-29
Can't enable 3d effects on lucid lynx even if restricted nvidia driver (v195.36.24) is  installed and activated.

Actually 3D effects were working with compiz etc, but at a given moment -not sure if after the final release of the 10.04 - they stopped working, and now it always fails to enable them.

Cheers,
uFrank

---

### Post by meditatingfrog on 2010-08-29
> **uFrank said:**
> Can't enable 3d effects on lucid lynx even if restricted nvidia driver (v195.36.24) is  installed and activated.

Actually 3D effects were working with compiz etc, but at a given moment -not sure if after the final release of the 10.04 - they stopped working, and now it always fails to enable them.

Cheers,
uFrank

I'm thinking you might want to try using an older kernel.  You should be able to select it from the grub boot screen, see if that fixes it.  If it does fix it, create a bug in launchpad that compiz with your nvidia controller works with kernel 2.6.x but not 2.6.y.

---

