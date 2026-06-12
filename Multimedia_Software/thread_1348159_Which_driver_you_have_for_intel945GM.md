---
title: "Which driver you have for intel945GM ?"
date: 2009-12-06
forum: Multimedia Software
---

### Post by baskar007 on 2009-12-06
I have karmic with all altest updates.

xorg eats lot of CPU resource and total system performance incredibly slow. I had used xorg stable PPA updates but its not solve the problem.
Just redisplaying the console-screen for top uses 70% CPU power, moving a window will lead to 100%, new windows need about 10 seconds to be displayed. This is unbearable! .

noticed in xorg0.log:
```

drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "i915"
(EE) intel(0): [drm] Failed to open DRM device for : No such file or directory
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): Failed to initialize kernel memory manager 

```

Bugged here :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/493435](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/493435)


if you are using 945GM with out any problems please tell me which video driver(version),mesa etc...  you are using ?

or there are any other hacks or tricks for this ?

---

