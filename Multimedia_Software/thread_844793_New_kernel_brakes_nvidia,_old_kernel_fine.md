---
title: "New kernel brakes nvidia, old kernel fine"
date: 2008-06-29
forum: Multimedia Software
---

### Post by cokehabit on 2008-06-29
Being used to compiling my own kernels and things I find it strange that every other kernel update breaks nvidia. Usually i just install the nvidia kernel again over the old one so why isn't something happening when my kernel upgrades on Ubuntu?

I always get: ```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```no nvidia driver in restricted drivers manager and booting in "safe graphics mode"

What am i doing wrong?:confused:

---

### Post by cokehabit on 2008-06-30
This must be a common problem

---

### Post by mcduck on 2008-07-01
HAw didi you install the nVidia drivers in the first place? If they are not from the repositories, they need a kernel module (that of course depends on certain kernel version). So if the drivers are not from repositories you need to install new version of that module yourself.

If you use the driver from repositories, and have correct metapackage for your kernel ("linux-generic", for example) installed the driver shouldn't break during kernel updates.

---

### Post by cokehabit on 2008-07-01
> **mcduck said:**
> HAw didi you install the nVidia drivers in the first place? If they are not from the repositories, they need a kernel module (that of course depends on certain kernel version). So if the drivers are not from repositories you need to install new version of that module yourself.

If you use the driver from repositories, and have correct metapackage for your kernel ("linux-generic", for example) installed the driver shouldn't break during kernel updates.

They were all from the repos and the metapackage is -generic and not -386

For some reason it always breaks. Currently I have to use my old kernel even though the metapackage and headers are from the same kernel the nvidia.ko module will not load and therefore is not seen by restricted drivers.

---

### Post by sdennie on 2008-07-01
So, you have the nvidia-glx-new package installed or you installed by downloading the drivers from the website?  Do you have the proposed repo enabled in System->Administration->Software Sources?

---

### Post by cokehabit on 2008-07-01
> **vor said:**
> So, you have the nvidia-glx-new package installed or you installed by downloading the drivers from the website?  Do you have the proposed repo enabled in System->Administration->Software Sources?I have all 4 (main, restricted, universe, multiverse) selected

The packages that is installed is from apt/synaptic.

The only reason I can think of is that this is a problem from when Hardy went live (i've beta tested Ubuntu for ages).

Heh, after 5 years of Gentoo I would have thought i'd be able to figure out this one but I just can't! [-(

---

### Post by sdennie on 2008-07-02
A number of people have been having this problem and I'm not sure why.  I would first try rebooting into recovery mode and when the menu comes up try using the xfix option.  That may or may not work.

If you are coming from gentoo and don't mind taking some control over the system, you could follow this guide to manually install the nvidia driver: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270) and then use this guide to automatically install the manual drivers when new kernels are installed: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).  Unfortunately, they will still break when xserver-xorg-core is updated (X will still start normally but compiz won't) so, you'll have to reinstall the drivers whenever an update to that package happens.

---

### Post by p_quarles on 2008-07-02
Moved to Multimedia & Video.

---

### Post by steveingbg on 2008-07-02
I have the same problem. Nvidia driver installed from repositories, works in Hardy with kernel 2.6.24-17. After the system auto-updated to 2.6.24-19, nvidia driver doesn't work, falls back to safe graphics mode. I can still boot kernel 2.6.24-17 and everything works.

---

### Post by cokehabit on 2008-07-02
This is obviously a bug. I have seen it in hardy since before it was released. It is also present on my girlfriend's computer that although was installed *after* hardy was released was still installed from a beta disk but subsequently updated immediately.

There was a mix up before with the -i386 and the -generic headers but that was fixed.

Bug Report: [https://bugs.launchpad.net/ubuntu/+bug/244798](https://bugs.launchpad.net/ubuntu/+bug/244798)

---

### Post by cokehabit on 2008-07-04
for anyone else getting this problem do this:

purge (apt-get purge) linux-restricted-modules-common, linux-restricted-modules-generic and linux-restricted-modules-2.6.24-19-generic

then reinstall them

---

