---
title: "[SOLVED] Nvidia GLX extension not loading"
date: 2008-06-04
forum: Multimedia Software
---

### Post by Clean3d on 2008-06-04
Hello,
I installed the latest drivers from Nvidia's website to fix a problem I'd had with Blender, but now it is not loading the "GLX" extension.

I've searched around the forums, and it seems I have to disable "composite" in xorg.conf. So, I run

```
sudo nvidia-xconfig --no-composite
```

but I get the following error upon typing startx

```
   [   93.237308] NVRM: API mismatch: the client has the version 169.12, but
   [   93.237312] NVRM: this kernel module has the version 71.86.04.  Please
   [   93.237315] NVRM: make sure that this kernel module and all NVIDIA driver
   [   93.237318] NVRM: components have the same version.
```

I can get X to start by switching the drivers used in xorg.conf from "nvidia" to "nv", but then I can't use the GLX extensions. What gives?

Anyone know how to solve this?

---

### Post by prismatic7 on 2008-06-04
> **Clean3d said:**
> Hello,
I installed the latest drivers from Nvidia's website to fix a problem I'd had with Blender, but now it is not loading the "GLX" extension.

I've searched around the forums, and it seems I have to disable "composite" in xorg.conf. So, I run

```
sudo nvidia-xconfig --no-composite
```

but I get the following error upon typing startx

```
   [   93.237308] NVRM: API mismatch: the client has the version 169.12, but
   [   93.237312] NVRM: this kernel module has the version 71.86.04.  Please
   [   93.237315] NVRM: make sure that this kernel module and all NVIDIA driver
   [   93.237318] NVRM: components have the same version.
```

I can get X to start by switching the drivers used in xorg.conf from "nvidia" to "nv", but then I can't use the GLX extensions. What gives?

Anyone know how to solve this?

You shouldn't have to disable composite at all! Just make sure you remove the nvidia-glx package, and possibly linux-restricted-modules, then reboot (in recovery mode) and reinstall the Nvidia driver.

---

### Post by Clean3d on 2008-06-04
Everything seems to be working now. 8) Thank you so much!

One last question: I can understand why I needed to remove the packages, but why is recovery mode important? (I'm still learning ;))

---

### Post by Unix_Slayer on 2008-06-04
> **Clean3d said:**
> Everything seems to be working now. 8) Thank you so much!

One last question: I can understand why I needed to remove the packages, but why is recovery mode important? (I'm still learning ;))


It depends. I installed my NVidia driver after control+alt+backspace. Worked fine for me. Also... multiple drivers will cause this ==>[   93.237308] NVRM: API mismatch: the client has the version 169.12, but
   [   93.237312] NVRM: this kernel module has the version 71.86.04.  Please
   [   93.237315] NVRM: make sure that this kernel module and all NVIDIA driver
   [   93.237318] NVRM: components have the same version.

---

### Post by Domie on 2008-07-13
> **Unix_Slayer said:**
> It depends. I installed my NVidia driver after control+alt+backspace. Worked fine for me. Also... multiple drivers will cause this ==>[   93.237308] NVRM: API mismatch: the client has the version 169.12, but
   [   93.237312] NVRM: this kernel module has the version 71.86.04.  Please
   [   93.237315] NVRM: make sure that this kernel module and all NVIDIA driver
   [   93.237318] NVRM: components have the same version.

I have the same problem. Every time I reinstall the nvidia driver from the nvidia website, I can start an X session (startx or by kdm).

When I reboot, I get a blank screen and I have to reinstall the nvidia driver again and again (tty login), but then it works again (till I reboot of course).

The only problem there is mentioned is this API mismatch.

---

### Post by zooounds on 2008-07-29
I have the same problem, I try to switch to the Ubuntu version from the Nvidia-home-page-version. It won't work.

---

