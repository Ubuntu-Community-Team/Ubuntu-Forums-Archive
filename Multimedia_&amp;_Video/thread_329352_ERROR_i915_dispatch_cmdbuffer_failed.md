---
title: "*ERROR* i915_dispatch_cmdbuffer failed"
date: 2007-01-01
forum: Multimedia &amp; Video
---

### Post by rramalho on 2007-01-01
Hi all!

I have an Intel DG965WH mainboard, and managed to install Ubuntu **Edgy** on it using an external DVD-RW drive connected to the USB port. I still have to install the Marvell patch to access P-ATA drives...

But i want to install other things first! For instance i would like to run accelerated OpenGL programs and I'm having this weird problem:

```
rramalho@xxxxxx:~$ glxgears 
libGL warning: 3D driver claims to not support visual 0x5a
DRM_I830_CMDBUFFER: -22
rramalho@xxxxxx:~$ ./googleearth 
libGL warning: 3D driver claims to not support visual 0x5a
DRM_I830_CMDBUFFER: -22
rramalho@xxxxxx:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x5a
direct rendering: Yes
```

When i do a "dmesg" i see this:

```
rramalho@xxxxxx:~$ dmesg | tail -n 2
[17263972.928000] [drm:i915_cmdbuffer] *ERROR* i915_dispatch_cmdbuffer failed
[17263978.580000] [drm:i915_cmdbuffer] *ERROR* i915_dispatch_cmdbuffer failed
```

I'm using the onboard graphics. The intel G965.

Can anyone help? Thank you all!

---

