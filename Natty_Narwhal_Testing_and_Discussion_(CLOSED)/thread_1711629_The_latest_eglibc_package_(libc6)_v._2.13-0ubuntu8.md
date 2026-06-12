---
title: "The latest eglibc package (libc6) v. 2.13-0ubuntu8"
date: 2011-03-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-03-21
The latest eglibc package (2.13-0ubuntu8) may cause problems.
Synaptic may offer to remove a number of important packages from your system.
This happens if you do not first install this new package:
 - multiarch-support (2.13-0ubuntu8)

The reason is that the previous eglibc, and particularly libc6 provided the virtual package *multiarch-support*.
However, the libc6 version  2.13-0ubuntu8 does not do that anymore.
So you need to install it separately:

  ```
 debian/control.in/libc, debian/control.in/main: make multiarch-support a
    real package depending on the native libc; this eliminates the problem
    of a circular depends/pre-depends loop never permitting apt to install
    the base libraries for any foreign architecture.  We still have the
    dependency loop for the native architecture, which is safe (and needs to
    be enforced!), but whenever a package is installed non-native, it's ok
    to bypass this requirement (which is effectively what we're doing by
    making multiarch-support Multi-Arch: foreign), because none of the
    concerned library packages are installable at all unless a Multi-Arch:
    same libc6 is available.
```

---

### Post by portis on 2011-03-22
Thanks!

> **Harry33 said:**
> The latest eglibc package (2.13-0ubuntu8) may cause problems.
Synaptic may offer to remove a number of important packages from your system.
This happens if you do not first install this new package:
 - multiarch-support (2.13-0ubuntu8)

The reason is that the previous eglibc, and particularly libc6 provided the virtual package *multiarch-support*.
However, the libc6 version  2.13-0ubuntu8 does not do that anymore.
So you need to install it separately:

  ```
 debian/control.in/libc, debian/control.in/main: make multiarch-support a
    real package depending on the native libc; this eliminates the problem
    of a circular depends/pre-depends loop never permitting apt to install
    the base libraries for any foreign architecture.  We still have the
    dependency loop for the native architecture, which is safe (and needs to
    be enforced!), but whenever a package is installed non-native, it's ok
    to bypass this requirement (which is effectively what we're doing by
    making multiarch-support Multi-Arch: foreign), because none of the
    concerned library packages are installable at all unless a Multi-Arch:
    same libc6 is available.
```

---

