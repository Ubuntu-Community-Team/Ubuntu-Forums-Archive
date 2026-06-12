---
title: "Nvidia driver Problems"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by TheSqueak on 2005-10-16
Hiya,

i've just installed Breezy Badger, and i'm having some trouble getting the nvidia drivers to actually load up X properly.

When I try and start my display manager it just drops out and leaves me back at the console.

*From /var/log/Xorg.0.log*
> (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

> $ lsmod | grep nvidia
nvidia               3711364  0
nvidia_agp              7964  1
agpgart                32328  2 nvidia,nvidia_agp

*From dmesg*
> [4307653.820000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4308760.141000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7676  Fri Jul 29 12:58:54 PDT 2005
[4308823.274000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7667  Fri Jun 17 07:01:04 PDT 2005
[4308823.275000] NVRM: RM/client version mismatch!!
[4308823.275000] NVRM:    aborting to avoid catastrophe!
[4308853.296000] NVRM: RM/client version mismatch!!
[4308853.296000] NVRM:    aborting to avoid catastrophe!

How is it that i've ended up trying to load 2 different versions of the nvidia module?

---

### Post by scorpioxy on 2005-10-16
Had the same problem. I was just working on it. Although in mine, it was trying to load module 7667 while the compiled module from the installer was 7676. My temporary fix was to download 7667 from nvidia and run its installer. I am still  looking to see how can i force it to only load 7676. I will update if there is any change.

---

### Post by hone on 2005-10-16
I think it means the nvidia-kernel-common package and the nvidia compiled modules are in conflict.  I ran into this problem.  I still don't ahve direct rendering working but I have X working.  I either had ot update nvidia-kernel-common or d/l the kernel-source and the kernel headers and compile my own module and load it with make-kpkg modules_image.

---

### Post by pvoce on 2005-10-16
Ive run into close to the same problem myself.  I have the latest driver for my card, but there appears to be a conflict whilt trying to compile it. Also, while trying to remove all of the deb nvidia pacakges, I get stuck on the nvidia-glx package with the following error messge: 

E: nvidia-glx: subprocess post-removal script returned error exit status 2

While looking at the terminal, I get the following explanation:

dpkg-divert: rename invloves overwriting '/usr/lib/libGL.so.1.2' with different files '/usr/lib/libGL.so.1.2.xlibmesa'  not allowed

I dont have these packages, and dont know which ones they came with, as I cant find them in synaptic.

Any ideas?

---

### Post by TheSqueak on 2005-10-17
Fixed it.

I downloaded version 7667 of the nvidia driver from nvidia and installed that, and now it works.

Now I just need to work out why i'm only getting 11fps with glxgears :)

---

### Post by wylfing on 2005-10-17
I am pretty sure glxgears isn't functional as a benchmark for a lot systems now. A large number of people who were getting thousands of FPS on glxgears now get only double digits.

Try a real game, and see how the performance is.

If you get horrible performance in a real game, I would suggest you should not have nvidia_agp and agpgart both loaded at the same time. They're probably conflicting with each other.

---

