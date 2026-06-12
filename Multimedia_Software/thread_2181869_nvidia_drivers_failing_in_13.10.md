---
title: "nvidia drivers failing in 13.10"
date: 2013-10-19
forum: Multimedia Software
---

### Post by rogervn on 2013-10-19
I'm trying to use the new nvidia-drivers with nvidia-prime, but I am not having any success.

I have a GTX 670M laptop with a Ivy Bridge processor with Optimus Support.

First I'd tried to install the nvidia-319 drivers along with nvidia-prime. As I rebooted I was greeted with a lot of errors messages, choppy screen updating and no desktop effects. Window decoration also looked like a old blue one.

Then I purged them all and went back to stock intel drivers, everything was OK.

Then I tried again the nvidia-319 drivers without the nvidia-prime.

Then I got to lightdm, but as soon as I logged in, the screen would turn black and just freeze.

Also tried a third-party repository for nvidia-325 with and without nvidia-prime. Same problems.

I've also noticed these error messages in Xorg log:

```
[   291.700] (EE) Failed to load /usr/lib/xorg/modules/libglamoregl.so: /usr/lib/xorg/modules/libglamoregl.so: undefined symbol: _glapi_tls_Context
[   291.700] (EE) Failed to load module "glamoregl" (loader failed, 7)

```

---

### Post by georeth on 2013-10-19
Same problem with GT550M on my lenovo Y470 laptop. I just installed nvidia-319 and now X starts in fallback mode.

Xorg log follows:

```

[    34.147] (II) Loading /usr/lib/xorg/modules/libglamoregl.so[    35.725] (EE) Failed to load /usr/lib/xorg/modules/libglamoregl.so: /usr/lib/xorg/modules/libglamoregl.so: undefined symbol: _glapi_tls_Context
[    35.725] (II) UnloadModule: "glamoregl"
[    35.725] (II) Unloading glamoregl
[    35.725] (EE) Failed to load module "glamoregl" (loader failed, 7)
[    35.725] (II) LoadModule: "glx"
[    35.726] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    36.111] (II) Module glx: vendor="NVIDIA Corporation"
[    36.111]     compiled for 4.0.2, module version = 1.0.0
[    36.111]     Module class: X.Org Server Extension
[    36.111] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:55:38 PDT 2013
[    36.129] Loading extension GLX
[    36.129] (II) LoadModule: "nvidia"
[    36.130] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    36.449] (II) Module nvidia: vendor="NVIDIA Corporation"
[    36.449]     compiled for 4.0.2, module version = 1.0.0
[    36.449]     Module class: X.Org Video Driver
[    36.535] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 14:34:12 PDT 2013
[    36.535] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    36.564] (++) using VT number 7


[    36.564] (EE) No devices detected.



```

---

### Post by Yellow Pasque on 2013-10-19
Yes, installing the nvidia drivers directly on an Optimus laptop will bork the intel driver (it's a n00b trap). Unless you're always going to be hooked to AC, forget nvidia-prime and use Bumblee: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by rogervn on 2013-10-22
But nvidia drivers alone also don't work.

---

### Post by v1k1ng1001 on 2013-10-23
nvidia-prime overheated my 610m.  Swapped nvidia-prime for bumblebee and everything works.  I am using Ubuntu Gnome so no conflict with lightdm.

---

### Post by Linuxisfast on 2013-10-23
> **Rogrio_Vinhal_Nunes said:**
> I'm trying to use the new nvidia-drivers with nvidia-prime, but I am not having any success.

I have a GTX 670M laptop with a Ivy Bridge processor with Optimus Support.

First I'd tried to install the nvidia-319 drivers along with nvidia-prime. As I rebooted I was greeted with a lot of errors messages, choppy screen updating and no desktop effects. Window decoration also looked like a old blue one.

Then I purged them all and went back to stock intel drivers, everything was OK.

Then I tried again the nvidia-319 drivers without the nvidia-prime.

Then I got to lightdm, but as soon as I logged in, the screen would turn black and just freeze.

Also tried a third-party repository for nvidia-325 with and without nvidia-prime. Same problems.

I've also noticed these error messages in Xorg log:

```
[   291.700] (EE) Failed to load /usr/lib/xorg/modules/libglamoregl.so: /usr/lib/xorg/modules/libglamoregl.so: undefined symbol: _glapi_tls_Context
[   291.700] (EE) Failed to load module "glamoregl" (loader failed, 7)

```


Did you install linux-headers-generic? nvidia prime works fine here but the laptop runs hot and uses more battery. Also no control for gamma or brightness possible.

---

