---
title: "gdm won't start, plymouth just wont let go"
date: 2010-11-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SevenMachines on 2010-11-28
I was wondering if anyone else sees this problem, gdm cant start because plymouth blocks it. Even if splash is disabled, the plymouthd is always running and blocks gdm anyway (EDIT: gdm will start if plymouthd is killed so it does seem to be the culprit). I've just purged all plymouth packages for the moment but i wanted to see if anyone else gets this.
this computers a bit 'non-standard' at the moment so i dont want to file a bug if its just me until i've re-installed 

> 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
> (WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading /usr/lib/xorg/modules/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.9.0.902, module version = 0.0.2
(EE) intel(0): [drm] failed to set drm interface version.
(EE) intel(0): Failed to become DRM master.
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) intel(0): Chipset: "945GM"
DRM_IOCTL_I915_GEM_APERTURE failed: Bad file descriptor
Assuming 131072kB available aperture size.
May lead to reduced performance or incorrect rendering.
get chip id failed: -1 [9]
param: 4, val: 0
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): video overlay key set to 0x101fe
(EE) intel(0): failed to get resources: Bad file descriptor
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


---

### Post by dino99 on 2010-11-28
hi,
dont have met this problem with nvidia x-swat on i386, only compiz issue: previously was not installed because i've not much time to spend with incoming unity troubles, but now the system need it to be installed (activated as normal) otherwise borders and decorations are left.

---

### Post by garvinrick4 on 2010-11-29
Not to sure removing plymouth does not break gdm
```
rick@rick-laptop:/$ sudo aptitude show plymouth
Package: plymouth                        
State: installed
Automatically installed: no
Version: 0.8.2-2ubuntu5.1
Priority: required
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 475 k
Depends: libc6 (>= 2.8), libdrm-intel1 (>= 2.4.9), libdrm-nouveau1 (>=
         2.4.20-3~), libdrm-radeon1 (>= 2.4.17), libdrm2 (>= 2.4.3),
         libplymouth2 (= 0.8.2-2ubuntu5.1), upstart-job, udev (>= 149-2),
         mountall (>= 2.0), initramfs-tools
Recommends: plymouth-theme-ubuntu-text | plymouth-theme
Conflicts: usplash
Breaks: gdm (< 2.29.1-0ubuntu4), kdm (< 4:4.4.2-0ubuntu6),
        lubuntu-plymouth-theme (<= 0.4), ubuntustudio-plymouth-theme (<= 0.38),
        xubuntu-plymouth-theme (< 10.04.4)
Description: graphical boot animation and logger - main package
 Plymouth is an application that runs very early in the boot process (even
 before the root filesystem is mounted!) that provides a graphical boot
 animation while the boot process happens in the background.

rick@rick-laptop:/$ 

```

---

### Post by lucazade on 2010-11-29
> **garvinrick4 said:**
> Not to sure removing plymouth does not break gdm
```
rick@rick-laptop:/$ sudo aptitude show plymouth
Package: plymouth                        
State: installed
Automatically installed: no
Version: 0.8.2-2ubuntu5.1
Priority: required
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 475 k
Depends: libc6 (>= 2.8), libdrm-intel1 (>= 2.4.9), libdrm-nouveau1 (>=
         2.4.20-3~), libdrm-radeon1 (>= 2.4.17), libdrm2 (>= 2.4.3),
         libplymouth2 (= 0.8.2-2ubuntu5.1), upstart-job, udev (>= 149-2),
         mountall (>= 2.0), initramfs-tools
Recommends: plymouth-theme-ubuntu-text | plymouth-theme
Conflicts: usplash
Breaks: gdm (< 2.29.1-0ubuntu4), kdm (< 4:4.4.2-0ubuntu6),
        lubuntu-plymouth-theme (<= 0.4), ubuntustudio-plymouth-theme (<= 0.38),
        xubuntu-plymouth-theme (< 10.04.4)
Description: graphical boot animation and logger - main package
 Plymouth is an application that runs very early in the boot process (even
 before the root filesystem is mounted!) that provides a graphical boot
 animation while the boot process happens in the background.

rick@rick-laptop:/$ 

```

You can't remove Plymouth, it depends on MountAll.

What about adding one of these options to kernel (via grub)?
i915.modeset=0
or 
nomodeset

---

### Post by SevenMachines on 2010-11-29
> **lucazade said:**
> You can't remove Plymouth, it depends on MountAll.

What about adding one of these options to kernel (via grub)?
i915.modeset=0
or 
nomodeset
I modified the mountall source and defined away its plymouth specific  code to get a non-plymouth package version, then removed the plymouth  package. I dont have any problems with a straight text boot but i think a  reinstall might be better for testing purposes, i'll see what happens  then.
 i'd totally forgotten about nomodeset (doh!) thanks for the reminder

---

