---
title: "VLC showing errors after an update"
date: 2020-01-22
forum: Multimedia Software
---

### Post by maxbb on 2020-01-22
After an update, when I run VLC on Ubuntu 18.04 (64 bit) I see these errors:


```

libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Error: couldn't find RGB GLX visual or fbconfig
VLC media player 3.0.8 Vetinari (revision 3.0.8-0-gf350b6b)

[...]

[00007f1be4aeb280] glx gl error: cannot choose GLX frame buffer configurations

```

This happens with both "snap" and system versions of VLC. All other video-playing apps work fine (mplayer, Videos, Chrome)


I'm using Nvidia drivers though (from PPA). What can I do to fix this?

I asked in a VLC forum already, and was told that "[COLOR=#333333][FONT=&quot]Mesa tries to use the software rasterizer and fails. Your GL driver is not installed properly. "


[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-01-22
At first glance this information > [COLOR=#333333][FONT=&amp]Mesa tries to use the software rasterizer and fails. Your GL driver is not installed properly.[/FONT][/COLOR] seems correct, or at least very plausible.

What are your Nvidia graphics card model and proprietary drivers version? Also how exactly have you installed those drivers and have you disabled Secure Boot in UEFI?

---

### Post by maxbb on 2020-01-22
> **CelticWarrior said:**
> At first glance this information  seems correct, or at least very plausible.


mplayer, Videos and Chrome play videos without any issues though...

VLC can only play them in smallish windows (original resolution), but shows a black screen when maximized or in full-screen mode (4K)

I had the same hardware for 5 years, and never had this issue.

> 
What are your Nvidia graphics card model and proprietary drivers version?


NVIDIA GTX 750

```
nvidia-driver-440                440.33.01-0ubuntu1       amd64        NVIDIA driver metapackage
```


> Also how exactly have you installed those drivers 

```
deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 /
```

in ```
/etc/apt/sources.list.d/cuda.list
```

> and have you disabled Secure Boot in UEFI?

I don't recall doing that. It's not convenient to check at the moment.

---

### Post by CelticWarrior on 2020-01-22
If you don't disable Secure Boot the proprietary drivers won't be used even if installed.

---

### Post by maxbb on 2020-01-22
> **maxbb said:**
> After an update, when I run VLC on Ubuntu 18.04 (64 bit) I see these errors:[COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

... It might be that it was showing these errors before also, but it stopped working (when maximized) after I updated the Nvidia drivers (from 3XX to 440) and many other things with a "dist-upgrade"

---

### Post by maxbb on 2020-01-22
> **CelticWarrior said:**
> If you don't disable Secure Boot the proprietary drivers won't be used even if installed.

I must have disabled it then (or maybe my motherboard doesn't have it). I've been using Nvidia drivers on this machine for 5 years.

---

### Post by maxbb on 2020-01-23
[B]Update:

[/B]Can this be the cause of the problems?

  ***/usr/lib/x86_64-linux-gnu/libGL.so.1***

exists and belongs to **libgl1** (vendor-neutral library), BUT** libnvidia-gl-440** only includes these libraries

***/usr/lib/x86_64-linux-gnu/libEGL_nvidia.so.0***
***/usr/lib/x86_64-linux-gnu/libGLESv1_CM_nvidia.so.1***
***/usr/lib/x86_64-linux-gnu/libGLESv2_nvidia.so.2***
***/usr/lib/x86_64-linux-gnu/libGLX_nvidia.so.0***
***/usr/lib/x86_64-linux-gnu/libnvoptix.so.1***
***/usr/lib/x86_64-linux-gnu/nvidia-440/xorg/libglxserver_nvidia.so***


(no l**ibGL.so**)

---

### Post by maxbb on 2020-02-04
Looks like this has been fixed. (The version in `snap` is still broken) Both are 3.0.8

---

